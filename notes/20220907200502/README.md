# Action Types

## One Record

- Execute the action individually in one record
- We can select multiple records
  - But it will trigger one action for each record

```js
function (record, oldRecord, action) {
}
```

## Many Records

- It execute the action only once
  - No matter we have several records selected
- It will accomplish the criteria of UI filters

The function will have a `query` which is a `sys.data.Query` instance.
You need to use `sys.data.find(query)` to get the Result Set.

```js
function (query, action) {
}
```

## Global Action

- It is no related to any record

**Parameters**

```js
function (action) {
}
```
