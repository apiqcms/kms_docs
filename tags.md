## declare
Tag declare could be used for variables declaration and initial value setup in this form:

&#123;% declare var = expr %&#125;

Difference between declare and assign tag - with declare you can create variables with the same names but in different scopes.

## assign
Tag assign could be used for variables declaration and its initial value setup in this form:

&#123;% assign var = expr %&#125;

## if
Tag if is a standard conditional statement and has this form:

&#123;% if cond-1 then: %&#125;

  code-1

[&#123;% elsif: cond-2 then: %&#125;

  code-2] ...

[&#123;% else: %&#125;

  code-else]

&#123;% end if %&#125;

## unless
Tag unless executes its "body" if conditional expression results in false or null:

&#123;% unless cond-1 then: %&#125;
  code-1
&#123;% end unless %&#125;

## for
Tag for is a standard cycle statement and has this form:&nbsp;

&#123;% for var in: list do: %&#125;
  code
&#123;% end for %&#125;
&#123;% for var from: lower-limit to: upper-limit do: %&#125;
  code
&#123;% end for %&#125;

## capture
Tag capture runs code and saves result in var. If var already contained value, capture changes it:

&#123;% capture var = %&#125;
  code
&#123;% end capture %&#125;

## content_for
Tag content_for runs code and saves result in some handle:

&#123;% content_for "handle" capture: %&#125;
  code
&#123;% end content_for %&#125;

## yield
Tag yield has 3 forms. In the simples case (without arguments) it inserts content of internal template (Page content in terms of this CMS). If string with handle was setup with &#123;% content_for %&#125;, then yield returns this string. If no string with handle, yield returns result of if_none block execution, if such block was specified, or just empty string:

&#123;% yield %&#125;
  Or
&#123;% yield "handle" %&#125;
  Or
&#123;% yield "handle" if_none: %&#125;
  code
&#123;% end yield %&#125;

## include
Tag include includes content of Snippet into template. The only argument of include - Snippet ID (field "Slug/ID" that you need to setup on Snippet creation in "Snippets"):

&#123;% include "partial_name" %&#125;
