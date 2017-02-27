## var_loop
Variable giving access to current state of cycle/iteration. Can be used only in "for" cycle. var_loop - common name, for accessing actual cycle variable you need to concatenate cycle variable name and "_loop". Example:

&#123;% for p in: index.children do: %&#125;

  &#123;&#123; p_loop.index &#125;&#125; # prints number of current iteration

Property of var_loop	| Description
        ---           |    ---
length | Iterations count (collection size)
index | Current iteration index - index of element
rindex | length - index - 1
is_first | index == 0
is_last | index == length - 1
