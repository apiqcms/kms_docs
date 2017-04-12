## asset_path
Filter `asset_path` allows to get a relative path to any file from "Assets" section by filename:

```handlebars
<img src="{{ 'logo.png' | asset_path }}">
```

## asset_tag
Filter `asset_tag` allows to include javascript and css files, uploaded to "Assets" section:

```handlebars
{{ 'bootstrap.min.css' | asset_tag }}
```

## resize
This function/filter helps to change image size on-the-fly. For this filter you need to use absolute URL of image and "format" argument. Returns also URL. To get absolute URL (having only relative - any asset from "Assets") you should use `request.base_url`:

```handlebars
{{ 'http://example.com/image.png' | resize format: '100x100' }}
{{ (request.base_url + item.image) | resize format: '100x100' }}
```

## add_watermark
It allows to add watermark to image. You need image URL and 3 arguments: "image" - watermark image (watermark), "dissolve" - transparency and "position" - position. Returns also URL:

```handlebars
{{ 'http://example.com/image.png' | add_watermark image: 'http://example.com/watermark.png' dissolve: '50%' position: 'center' }}
```

## ends_with
Allows to check if string ends with some pattern:

```handlebars
{% if ends_with(media_item.file pattern: 'mp4') then: %}
```

## currency
Formats currency values. Possible options: precision, delimiter, separator, format, unit:

```handlebars
# item.price is 100.0
{{ item.price | currency precision: 0 }}
# result - "100 руб."
```
