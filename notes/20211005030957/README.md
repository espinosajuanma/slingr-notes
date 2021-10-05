# Data and Metadata

- **Data**: This are all the records and data stored on the app
- **Metadata**: All the definition of the application: entities,
  actions, scripts...

## Sync

When we make a sync from one environment to other it just pass the
metadata.

## Don't assume we have a record on all environments

```js
record.findById('myEntity', '1234');
```

With this we create a metadata dependent of a data record.

## Enums

The only time we can do this is when the entity is defined like an Enum.

If this is the case the data of the entity is going to be sync from
`dev` to `staging`.

## General rule

The code shouldn't do a reference to a particular record except this is
an Enum.
