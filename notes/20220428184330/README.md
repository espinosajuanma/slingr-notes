# Wrap values in queries if they have a comma

This week I was totally confused because I had an issue trying to get
records that matches a value kinda like: `code,Name`.

Slingr will treat that comma as an "OR" operator. How could I forget
that??? So dumb!

This query will find all records with `uniqueCode` field equals to `xyz`
OR `Secret`.

```js
var records = sys.data.find('entityName', {uniqueCode: 'xyz,Secret'});
```

Instead if the record I am looking for has to match exactly for
`xyz,Secret` I have to wrap it with the quotes... I am so annoyed of
overlook this detail.

```js
var records = sys.data.find('entityName', {uniqueCode: '"xyz,Secret"'});
```

> 📘 **Docs:**
>
> Keep in mind that if the value you are matching already has a comma
> you will need to wrap it using double quotes

- Reference:
  https://platform-docs.slingr.io/app_development_query_language.html#filters-by-field
