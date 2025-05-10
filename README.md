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

In the selected cell `B3`, `=SEQUENCE(ROWS(FILTER(C:C, C:C<>""))-1)`was entered. The formula `FILTER(C:C, C:C<>"")` oversees a specified range (i.e. `C:C`), then filters it to include only the non-empty rows using the condition `C:C<>""`. 

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

# Indexing Using Summation (Cumulative Counting) Based on Criterion 
![image](https://github.com/user-attachments/assets/28bfec64-5521-4491-bde0-c4da9f9690cb)
`=countifs($D$3:$D3, D3)`

In the selected cell `B3`, `=countifs($D$3:$D3, D3)` was entered. The `criteria_range1` is `$D$3:$D3`, wherein `$D$3` is an absolute reference to the starting point of the range. At row 3, `=COUNTIFS($D$3:$D3, D3)` becomes `=COUNTIFS(D3:D3, D3)`, counting the number of cells in the range `D3:D3` are equal to the value in `D3`. The first occurrence of a specific value under column D will then be indexed as `1` on column `B`, where the formula is entered. The formula can be dragged down to account for other data. In that case, at cell `B4`, the formula will be `=COUNTIFS($D$3:$D4, D4)`, counting the number of cells in the range `D3:D4` that are equal to the value in `D4` (`M`), which is `2`. In the event that the value at `D4` is different from that of `D3` (e.g. `F`), the count will be `1`.

# Converting Currency
![image](https://github.com/user-attachments/assets/c4b668bb-074b-4aea-87bc-5f724c12927d)

`=GOOGLEFINANCE("CURRENCY:USDPHP")*1615`

In the selected cell, `=GOOGLEFINANCE("CURRENCY:USDPHP")*1615` was entered. The `ticker` `"CURRENCY:USDPHP"` allows one to convert 1 US Dollar (USD) to Philippine Pesos (PHP) using the current exchange rate as retrieved from Google Finance. The exchange rate is then multiplied by 1615, converting USD 1615 to its equivalent value in PHP.

```
=GOOGLEFINANCE(ticker, [attribute], [start_date], [end_date|num_days], [interval])
```

|Parameter| Explanation |
| -------- | ----------- |
|`ticker`| |
|`[attribute]`| |
|`[start_date]`| |
|`[end_date|num_days]`| |
|`[interval]`| |


# Formatting Currency
![image](https://github.com/user-attachments/assets/229728c2-e153-41ef-9493-6370ff7fc226)
<kbd>Format</kbd> → <kbd>Number</kbd> → <kbd>Custom number format</kbd> `_("₱"* #,##0.00_);_("₱"* \(#,##0.00\);_("₱"* "-"??_);_(@_)` → <kbd>Apply</kbd>

# Concatenate

![image](https://github.com/user-attachments/assets/94060d56-b0f8-4942-a04a-e6a05af4e375)
`=CONCATENATE(C3, ", ", D3, " ", LEFT(E3,1), ".")`

In the selected cell, `=CONCATENATE(C3, ", ", D3, " ", LEFT(E3,1), ".")` was entered. The desired full name format is as follows: Last Name, First Name M., where M. refers to middle initial. The `CONCATENATE()` function works by appending multiple strings to one another, namely, the string from cell `C3`, a comma followed by a space `", "`, the string from cell `D3`, a space `" "`, a trimmed string by taking the first character from the left using `LEFT(E3,1)`, and a period `"."`).

#### LEFT() Syntax

#### CONCATENATE() Syntax

