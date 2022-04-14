# Enable `Global Actions` on Grid View

Today I run into an issue that the global action I was setting up
doesn't appear on the view.

I thought it was a permission thing, some kind of condition... But
nothing worked.

After a while I check the view settings and I saw it:

- `Show global actions` parameter set to `None`

I just changed to `All`. Also I can set it to `Some` and select the ones
I want to show.

You always can find a sneaky option parameter in slingr.
