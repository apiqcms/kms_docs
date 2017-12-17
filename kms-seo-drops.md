## seo
Object `seo` gives access to SEO properties of current page (or object). You can specify these properties in "SEO" section while editing your Page. If you have a Templatable Page (with enabled "Use as object template" option) and APIQ Models installed, you would probably want to have "title", "description" and etc. specified for each Model entry. And APIQ SEO still works for this: just follow a convention of adding special text fields to your Model: "seo_title", "seo_description", "seo_keywords" and "seo_h1" - and `seo` object for item/entry page will show you a content of these fields.

```handlebars
<title>{{ seo.title }}</title>
<meta name="keywords" content="{{ seo.keywords }}">
<meta name="description" content="{{ seo.description }}">
...
<h1>{{ seo.h1 }}</h1>
```

Property of `seo`	| Description
        ---           |    ---
title | Content for `<title>` tag
keywords | Content for `<meta name='keywords'...` tag
description | Content for `<meta name='description'...` tag
h1 | Content for page main header (`<h1>`)
