# google-sheets

# How to do dynamic indexing (1, 2, 3)

```
=ROW()
```

Explanation: 

| `ROW()` | Returns the row number, that is exactly the same as the row heading, which is typically visible on any spreadsheet application interface.
   
```
=ROW()-2
```

Explanation: 

`ROW()`: Returns the row number.
`-2`: Accounts for the two rows above (empty row for visual clearance and header).

```
=SEQUENCE(ROWS(FILTER(C:C, C:C<>""))-1)
```

Syntax

| C:C<>""  |     |
| February | $80     |
| March    | $420    |
