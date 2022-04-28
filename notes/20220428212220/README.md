# Use only string values for Dynamic Choice

Dynamic Choices are confusing already. Instead of setting actually a
value you have to give this object notation with all the options and the
`selectedValue`.

Not only that... You also have to remember (instead all conventions)
that options has a `label` AND a `name` (which in reality would be the
value).

Now we learn that values (in this case "names") they have to be strings.
I had to cast the numbers for strings and cast the selected value back
to Number when doing a custom validation.

- [Field type: `Dynamic choice`](/notes/20220309200706)
