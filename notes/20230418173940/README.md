# Use query parameters to filter a grid view

Diego Gonzalez just showed me that you can use a grid view link and pass
a parameter to grid filter.

```
/runtime/#views/{gridViewId}?type=daily
```

This will show you a list of the records with type `daily`.

The grid view is going to fill the `type` column filter with the value
you pass on. So the user can remove it later and see the rest of the
records.
