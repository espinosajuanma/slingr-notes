# Avoid enabling `Saving Linked Parameters` in actions if you can

Having this option enabled it triggers a Save in the record itself
before running the action code.

This can be expensive because it will trigger any `On Record Change`
listeners before actually running the action.

It doesn't matter you have a linked parameter or not. Joe told me that
as a general rule he always create an action he disabled "Saving Linked
Parameters" option. I'll try to follow this rule too.
