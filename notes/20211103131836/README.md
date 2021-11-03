# Websites integration

When we need to make a public website we can consume the API of the
SLINGR app importing the `slingr-ws.js` library.

[Website utils](https://github.com/slingr-stack/website-utils/tree/a915a2cebe1e0854ee04267114fe68e31bc590ea)

Also is important to setup an user for the permissions.

Steps:

1. Import `slingr-ws.js` library
1. Create a Group `Website`
  - Restrict permissions of writing
  - Check only read what is public
1. Create an user `Website`
  - Add it to the `Website` group
1. Add permission token in `Environment settings > API Tokens`
  - Set allowed domain
  - Set the user created
