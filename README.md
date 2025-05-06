# google-sheets

> [!NOTE]
> Parameters inside `[ ]` are OPTIONAL.

# Indexing Using Counting Numbers

## Using Cell Address

### Using ROW()

![image](https://github.com/user-attachments/assets/b25eeb86-833a-481f-9054-af2e5ddcb9b8)

`=ROW()`

In the selected cell `A1`, `ROW()` was entered. With an unspecified `cell_reference`, the formula returns the row number wherein the formula has been entered, leading to the value of `1`. The formula can be dragged/ copied to the subsequent rows, allowing them to follow the same principle (i.e. `A2` → `2`, `A3` → `3`, `A4` → `4`).

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

`=ROW()-2`

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

`=SEQUENCE(ROWS(FILTER(C:C, C:C<>""))-1)`

In the selected cell `B3`, `=SEQUENCE(ROWS(FILTER(C:C, C:C<>""))-1)`was entered. The formula oversees a specified range (i.e. `C:C`), then filters it to include only the non-empty rows using the condition `C:C<>""`. 

> [!NOTE]
> The "not equal" operator, represented by the symvol`<>` is used to compare two values and return a TRUE or FALSE.Therefore, `C:C<>""` checks whether each row within the `C:C` range is not equal to an empty string (represented as `""`), returning TRUE for every 

The `ROWS()` function then counts the number of filtered rows (i.e. non-empty rows). The `SEQUENCE()` function then spills a range of numbers from `1`, counting from the row wherein the formula was entered, up to the counted number of non-empty rows minus 1. As the range being checked is the entire column `C`, which contains a header row (i.e. a non-empty row), it is necessary to add `-1` at the end. Otherwise, specify the specific range to be filtered (e.g. `C3:C`) → `=SEQUENCE(ROWS(FILTER(C3:C, C3:C<>""))-1)`.

> [!WARNING]
> If there are *no* non-empty rows (i.e. entire `C:C` range is empty, a `#VALUE` error will be shown as `ROWS(FILTER(C:C, C:C<>""))` will output `0` → `0-1=-1`; however, the number of rows for the `SEQUENCE()` function must be `greater than or equal to 0`.

> [!CAUTION]
> While the indexing is dynamic, it will not be appropriate for sheets with blank in-between cells. Below is an example:

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