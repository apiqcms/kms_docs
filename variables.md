## var_loop
Variable giving access to current state of cycle/iteration. Can be used only in "for" cycle. var_loop - common name, for accessing actual cycle variable you need to concatenate cycle variable name and "_loop". Example:

```handlebars
{% for p in: index.children do: %}
  {{ p_loop.index }} # prints number of current iteration
{% end for %}
```

Property of var_loop	| Description
        ---           |    ---
length | Iterations count (collection size)
index | Current iteration index - index of element
rindex | length - index - 1
is_first | index == 0
is_last | index == length - 1
