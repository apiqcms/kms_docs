## POST /entries/:collection_name
This endpoint allows you to setup form submitting Model's elements. For example, if you have a model with collection name "posts" (and field with "title" Liquor name), you could create a form with action="/entries/posts" and an input with name="entry[title]"

```html
<form action="/entries/:collection_name" method="post">
  <input type="hidden" name='authenticity_token' value='{{ request.form_authenticity_token }}'>
  <input type="text" name="entry[name]">
  <input type="submit" value="Send">
</form>
```
