# google-sheets

> [!NOTE]
> Parameters inside `[ ]` are OPTIONAL.

# Indexing Using Counting Numbers

## Using Cell Address

### Using ROW()

![image](https://github.com/user-attachments/assets/b25eeb86-833a-481f-9054-af2e5ddcb9b8)

<lbs> =ROW() </kbd>

In the selected cell `A1`,`=ROW()` was entered. With an unspecified `cell_reference`, the formula returns the row number wherein the formula has been entered, leading to the value of `1`. The formula can be dragged/ copied to the subsequent rows, allowing them to follow the same principle (i.e. `A2` → `2`, `A3` → `3`, `A4` → `4`).

#### ROW() Syntax

```
=ROW([cell_reference])
```
|Parameter| Explanation |
| -------- | ----------- |
| `cell_reference` *(optional)* | The cell whose row number will be returned. (Default: Row where formula was entered.) |

> [!WARNING]
> If `cell_reference` is a range more than one cell wide and the formula is not used as an array formula, only the numeric value of the first row in `cell_reference` is returned.

### Using ROW() with Manual Row Adjustment for Data with Headers
![image](https://github.com/user-attachments/assets/445f926f-11a4-4f0b-8fed-a8b719031bd1)
```
=ROW()-2
```
In the selected cell `B3`, `=ROW()-2` was entered. The principle is similar to the previous (i.e. `B3` → `3`), with the main difference being the `-2` added at the end of the formula, which accounts for the two rows (i.e. empty row for visual clearance and header) above the row wherein the count starts. Consequently, `3-2=1`. The same formula can be dragged/ copied to the succeeding rows, allowing them to follow the same principle (i.e. `B4` → `4-2=2`, `B5` → `5-2=3`, `B6` → `6-2=4`).

#### ROW() Syntax

```
=ROW([cell_reference])
```
|Parameter| Explanation |
| -------- | ----------- |
| `cell_reference` *(optional)* | The cell whose row number will be returned. (Default: Row where formula was entered.) |

> [!WARNING]
> If `cell_reference` is a range more than one cell wide and the formula is not used as an array formula, only the numeric value of the first row in `cell_reference` is returned.

# Indexing With Blank In-Between Rows 

# Dynamic Indexing With Additional Rows (Added at the Bottom)

### Using FILTER(), ROWS(), and SEQUENCE()

```
=SEQUENCE(ROWS(FILTER(C:C, C:C<>""))-1)
```

#### FILTER() Syntax
```
=FILTER(range, condition1, [condition2, ...])
```

|Parameter| Explanation |
| -------- | ----------- |
`range` | The data to be filtered. |
`condition1` | A column or row containing true or false values corresponding to the first column or row of range, or an array formula evaluating to true or false. |
`[condition2 ...]` | Additional rows or columns containing boolean values TRUE or FALSE indicating whether the corresponding row or column in range should pass through FILTER. Can also contain array formula expressions which evaluate to such rows or columns. All conditions must be of the same type (row or column). Mixing row conditions and column conditions is not permitted. |

> [!IMPORTANT]
> Condition arguments must have exactly the same length as range.

#### ROWS() Syntax


C:C<>""

# Indexing Using Counting Numbers Based on Criterion 