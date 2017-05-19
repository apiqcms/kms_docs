## find_by
`find_by` allows you to find one element in collection by some condition/criteria.

```handlebars
{% assign news_page = index.children.find_by(title: 'News') %}
```

## find_all_by
`find_all_by` finds all collection elements matching criterias

```handlebars
{% for p in: index.children.find_all_by(published: true) do: %}
```

## except
`except` returns you all collection elements except ones provided as argument

```handlebars
{% assign correct_pages = index.children.except(excepted_page) %}
```

## find_except_by
`find_except_by` finds all collection elements not matching provided criterias

```handlebars
{% for p in: index.children.find_except_by(hidden: true) do: %}
```

## limit
`limit` method is equal to SQL limit so it allows to limit number of collection items

```handlebars
{% for post in: models.posts.limit(3) do: %}
```

## offset
`offset` method is equal to SQL offset so it allows to fetch records by offset

```handlebars
{% for post in: models.posts.limit(3).offset(3) do: %}
```

## first
returns first element in collection

```handlebars
{% assign first_post = models.posts.first %}
```

## last
returns last element in collection

```handlebars
{% assign last_post = models.posts.last %}
```

## []
returns element by its index

```handlebars
{% assign third_post = models.posts[2] %}
```

## pluck
returns collection containing elements specific field values (not full object)

```handlebars
{% for post_title in: models.posts.pluck('title') %}
```
