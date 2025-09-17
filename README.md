# PyramidGenerator
A practice project built in JavaScript that generates pyramids while demonstrating core programming concepts such as arrays, strings, functions, loops, and conditional statements.

## Declare the Pyramid Character

- Declares a constant character that will be repeated to form the pyramid body. Change this to any single character (or string) you want.
```js
const character = "!";

```
## Pyramid Height
- Number of rows in the pyramid (height). Here it's 10.

```js
const count = 10;
```

## Array Declaration with Initialization
```js
const rows = [];
```
- Creates an empty array rows that will hold each row's string (with spaces + characters).
## Inversion
```js
let inverted = false;
```
- A boolean flag. If false the rows are added in normal top-to-bottom order.
- If true rows are inserted at the front so the final printed pyramid is inverted (largest row first).
## PadRow
```js
  const padRow = (rowNumber, rowCount) => {
  return (
    " ".repeat(rowCount - rowNumber) +
    character.repeat(2 * rowNumber - 1) +
    " ".repeat(rowCount - rowNumber)
  );
};
```
- `padRow` builds a single centered row:
    - `' '.repeat(rowCount - rowNumber)` produces left padding spaces so the pyramid is centered.
    - `character.repeat(2 * rowNumber - 1)` produces the characters for that row (odd counts: 1, 3, 5, ...).
    - Right padding is the same as left padding so the string width is constant.
    - For `count = 10`, each row width = 2*count - 1 = 19 characters.
- `rowNumber`
    - Represents the current row index you are building.
    - It starts at `1` (top row) and increases until it reaches `rowCount`
    - It controls: How many characters go into that row
        - Row 1 → 1 character
        - Row 2 → 3 characters
        - Row 3 → 5 characters … etc.
- `rowCount`
    - Represents the total number of rows in the pyramid.

    - Used for:

    - Calculating how many spaces are needed to center each row.

    - Top row has the most spaces (rowCount - 1).

    - Bottom row has zero spaces.

    - Ensuring each row has the same total width = 2 * rowCount - 1

## For Loop
```js
for (let i = 1; i <= count; i++) {
  if (inverted) {
    rows.unshift(padRow(i, count));
  } else {
    rows.push(padRow(i, count));
  }
}
```
- Loop from `i = 1` (top row) up to `count` (bottom row).
- When `inverted === false` we `push` each new row to the end: rows become `[row1, row2, ..., row10]` → normal pyramid (small to large).
- When `inverted === true` we unshift (insert at front): after the loop rows become `[row10, row9, ..., row1]` → inverted pyramid (largest to smallest).

## Accumulate Result
```js
let result = "";

for (const row of rows) {
  result = result + row + "\n";
console.log(result);
}
```
- Initialize empty string to accumulate the full output.
- Iterate over each stored row and append it plus a newline to result. `(You could also do rows.join("\n") + "\n".)`
- Print the final multi-line pyramid to the console.





- 
