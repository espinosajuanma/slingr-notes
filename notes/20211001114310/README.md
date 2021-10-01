# User's permissions

Is easy to crash the security of the app with user's permissions.

## Sensitive permissions fields

There is sensitive fields like `groups`. If a group of users have
permissions to edit that field they can add themselves to any group.

This can be a problem because they change their permissions and escalate
privileges.

## Edit their own fields

There is other settings to limit what they can to edit.

Sometimes you need a group that can view all users, but we need to be
careful and set that fields we want to the user can edit but only on
their own user and not others.
