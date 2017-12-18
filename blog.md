Let's move to more complex example and learn how to make a blog using [APIQ CMS](https://www.apiq.io). Let's skip APIQ (and APIQ Models extension) installation steps and consider we already have blank CMS installation. By following steps below, you'll get fully functional blog.

## Pick HTML template

First, you need to have HTML either downloaded or prepared from scratch by HTML coder. I picked [this one](https://freehtml5.co/verb-free-html5-bootstrap-template-for-blog-websites/):

## Create first temlate

Ok, in downloaded template archive I have `index.html`. I'm going to use it as a template for blog index page.
Just paste html content, give template a name, and click "Add template".

![Create template](https://www.apiq.io/assets/apiq_blog_create_template.jpg)

## Upload assets

Now we need to upload all assets (under "Assets" section) we have in downloaded template, i.e. images, stylesheets and javascripts.
You could select multiple at once. For my template, I uploaded `js` folder content first, then `fonts`, `images` and `css`.

![Uploading assets](https://www.apiq.io/assets/apiq_blog_uploading_assets.jpg)

Now we need to fix fonts URLs (like `url("../fonts/icomoon/icomoon.eot")`) or other URLs in our stylesheets by inserting correct URLs from "Assets" section.

Next, let's find in template's content a place where page content should be injected and insert there special Liquor instruction `{% yield %}`. I'm going to insert it after `<div id="gtco-main"><div class="container">` and remove all content until closing tags.

## Create index page

Now let's create index page that uses just created template and paste there the content we've cut earlier from template. Once we have this in place, you should see something like this at website's root:

![Template created](https://www.apiq.io/assets/apiq_blog_template_created.jpg)

## Create first model

Next I'm going to make index page dynamic by introducing some models. First, I want main menu (`Develop`, `Business` and etc.) to represent blog categories. Let's create `Category` model under APIQ `Models` section.

![Create Categories](https://www.apiq.io/assets/apiq_blog_create_categories.jpg)

Now let's output categories as menu snippet. I extracted `<ul>...</ul>` from template into new snippet with "Menu" name and "menu" slug, and included this snippet in template with:

```handlebars
{% include 'menu' %}
```

And finally, I modified snippet like this (`name` is the only property I added to `Category` model, `permalink` is built-in property):
```handlebars
<ul>
  {% for category in: models.categories do: %}
    <li><a href="/{{ category.permalink }}">{{ category.name }}</a></li>
  {% end for %}
</ul>
```

## Create Post model

Ok, I can add categories and have dynamic menu based on them. Let's add second model - `Post` - and set up relationship between it and `Category` model.

![Create Posts](https://www.apiq.io/assets/apiq_blog_create_posts.jpg)

After this, I added one post belonging to "Development" category. Now I'm going to show the latest post as wide banner (as suggested by template design). I updated template's content like this (notice how I fetched the most recent post ):

```handlebars
{% assign recent_post = models.posts.order('created_at desc').first %}
<header id="gtco-header" class="gtco-cover" role="banner" style="background-image:url({{ recent_post.image }});" data-stellar-background-ratio="0.5">
  <div class="overlay"></div>
  <div class="container">
    <div class="row">
      <div class="col-md-7 text-left">
        <div class="display-t">
          <div class="display-tc animate-box" data-animate-effect="fadeInUp">
            <span class="date-post">{{ recent_post.created_at | strftime format: '%d %B %Y' }}</span>
            <h1 class="mb30">
              <a href="/{{ recent_post.permalink }}">{{ recent_post.title }}</a>
            </h1>
            <p><a href="/{{ recent_post.permalink }}" class="text-link">Read More</a></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</header>
```

And now, below this header I'd like to list all posts. This is the only content of index page for this purpose:
```handlebars
<div class="row row-pb-md">
  <div class="col-md-12">
    <ul id="gtco-post-list">
      {% for post in: models.posts.order("created_at desc") do: %}
        <li class="full entry animate-box" data-animate-effect="fadeIn">
          <a href="/{{ post.permalink }}">
            <div class="entry-img" style="background-image: url({{ post.image }})"></div>
            <div class="entry-desc">
              <h3>{{ post.title }}</h3>
              {{ post.preview }}
            </div>
          </a>
          <a href="/{{ post.category.permalink }}" class="post-meta">{{ post.category.name }}  <span class="date-posted">{{ post.created_at | strftime format: '%d %B %Y' }}</span></a>
        </li>
      {% end for %}
    </ul>
  </div>
</div>
```

![Index Page](https://www.apiq.io/assets/apiq_blog_index_page.jpg)

Index page should look like this (isn't it cool?).

## Create template pages for Category and Post models

This is our final step: we want to have category page and post page so our `permalink` properties will start working and point to concrete category or post. Let's create these 2 pages as children of index page. The most tricky thing here is to enable `Use as object template` property and choose representable object.

![Create Template Pages](https://www.apiq.io/assets/apiq_blog_create_template_pages.jpg)

Don't forget to put some html displaying Category and Product in corresponding pages. In these pages you have access to current object via `item` object. I.e. you could output post's content like this (on Post page):

```handlebars
<h1>{{ item.title }}</h1>
{{ item.content }}
```

On Category page there's one more trick for fetching current category's posts (because I used `belongs to` field):

```handlebars
{% assign posts = models.posts.find_all_by(category: item.id).order("created_at desc") %}
{% for post in: posts do: %}
...
```

And that's it - now I have completely dynamic and working Category page and Product page! And that's all for this tutorial: we have pretty basic blog functionality with a lot of possibilities to improve it further. For example, you might add `Published` field to `Post` model and list only published posts by default, or maybe introduce posts tagging. Your imagination is the only limit, so just try it ;-)

You could find my final result at: <a target="_blank" rel="nofollow" href="http://patient-forest-605.app.apiq.io">http://patient-forest-605.app.apiq.io</a>
