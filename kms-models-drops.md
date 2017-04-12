## models
Variable `models` gives access to models collections of entries. You can access collection using model collection name - "Collection name (for Liquor)" field. For example, if you created some Model with "services" collection name, then you could iterate its collection using "for" tag like this:

```handlebars
{% for service in: models.services do: %}
```
