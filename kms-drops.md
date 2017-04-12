## index
Variable `index` accessible in templates and references to root page (with "index" slug). Object properties are the same as for `page` variable.

```handlebars
{% for p in: index.children do: %}
  ...
{% end for %}
```

## page
Variable `page` can be accessed in any template and references to current page:

```handlebars
{{ page.title }}
```

Property of page	| Description
        ---           |    ---
slug | Value of "Slug" field
fullpath | Page fullpath
title | Value of "Title" field
published | Value of "Published" field
hidden | Value of "Hidden (from navigation)" field
templatable | Value of "Use as object template" field
children | Returns "children" collection - pages having this page as parent in "Parent page" field
parent | Parent page reference

## request
Variable `request` gives an access to some properties of current request:

```handlebars
{{ request.form_authenticity_token }}
```

Property of request	| Description
        ---           |    ---
path | Returns request relative path
url | Returns request URL
host | Returns host - domain name or IP address
base_url | Returns request root URL - protocol + domain name or IP, ex., "http://example.com"
referer | Returns URL of page that initiated current request
form_authenticity_token | Returns authenticity token for current request - for form protection from CSRF attack
param() | Returns URL param. Example: request.param('page')

## item
Variable `item` gives access to current object of "templatable" page. "Templatable" - page with enabled "Use as object template" field and chosen object in "Object" field. Properties of `item` depend on concrete object. Please check out [KMS Models](/kms-models)

```handlebars
{{ item.title }}
```
