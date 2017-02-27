## declare
Tag declare could be used for variables declaration and initial value setup in this form:

```handlebars
{% declare var = expr %}
```

Difference between declare and assign tag - with declare you can create variables with the same names but in different scopes.

## assign
Tag assign could be used for variables declaration and its initial value setup in this form:

```handlebars
{% assign var = expr %}
```

## if
Tag if is a standard conditional statement and has this form:

```handlebars
{% if cond-1 then: %}
  code-1
[{% elsif: cond-2 then: %}
  code-2] ...
[{% else: %}
  code-else]
{% end if %}
```

## unless
Tag unless executes its "body" if conditional expression results in false or null:

```handlebars
{% unless cond-1 then: %}
  code-1
{% end unless %}
```

## for
Tag for is a standard cycle statement and has this form:&nbsp;

```handlebars
{% for var in: list do: %}
  code
{% end for %}
{% for var from: lower-limit to: upper-limit do: %}
  code
{% end for %}
```

## capture
Tag capture runs code and saves result in var. If var already contained value, capture changes it:

```handlebars
{% capture var = %}
  code
{% end capture %}
```

## content_for
Tag content_for runs code and saves result in some handle:

```handlebars
{% content_for "handle" capture: %}
  code
{% end content_for %}
```

## yield
Tag yield has 3 forms. In the simples case (without arguments) it inserts content of internal template (Page content in terms of this CMS). If string with handle was setup with {% content_for %}, then yield returns this string. If no string with handle, yield returns result of if_none block execution, if such block was specified, or just empty string:

```handlebars
{% yield %}
  Or
{% yield "handle" %}
  Or
{% yield "handle" if_none: %}
  code
{% end yield %}
```

## include
Tag include includes content of Snippet into template. The only argument of include - Snippet ID (field "Slug/ID" that you need to setup on Snippet creation in "Snippets"):

```handlebars
{% include "partial_name" %}
```
