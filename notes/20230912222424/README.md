# Reminder with auto-refactoring on a new nested field

This would not happen for the REST API...

So if you create in the settings record a nested with this structure:

```json
{
  "contactForm": {
    "fieldA": null,
    "fieldB": null
  }
}
```

On the REST API it would be null or undefined

```json
{
  "contactForm": null
}
```

So accessing `settings.contactForm.fieldA` it will CRASH. Be aware of that tricky stuff next time you implement a new field and you use it with the api. Use optional chaining or check for null value before proceed.
