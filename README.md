# Week 4 — Code Screenshots

## Introduction

This README documents the screenshots inside the **Week 4 / screenshots** directory for the **PHP & MySQL Course (CA233)**. Week 4 is about **arrays** — the assignment file is titled *Question 1 - Arrays*. The work starts with a one-dimensional array of numbers that is processed with loops (printing it, totals, even/odd totals, minimum and maximum values and their positions), and then moves on to **two-dimensional (nested associative) arrays** that are displayed as HTML tables using `foreach`.

All of the Week 4 code lives in a single file, `assigment.php`, and the five screenshots below are consecutive portions of that file, so each screenshot is listed in the exact order it appears in the **Week4/screenshots** folder (`scr1.png` to `scr5.png`) and follows the same order as the code in the assignment.

| # | Filename | What It Covers |
|---|---|---|
| 1 | `scr1.png` | Creating the `$info` array, printing its elements, and calculating the total and the total of even elements |
| 2 | `scr2.png` | Total of odd elements, minimum element and its index, maximum element and its index |
| 3 | `scr3.png` | The `$colors` two-dimensional array and the start of the colors HTML table |
| 4 | `scr4.png` | The end of the colors table, and the `$classes` two-dimensional array |
| 5 | `scr5.png` | The `$classes` HTML table, built with `foreach` |

---

## 1. `scr1.png` — Creating the Array, Printing It, Total, and Total of Even Elements

![Array, Total, and Even Total Screenshot](scr1.png)

**What's in the image:** the start of the script — an array of 12 numbers called `$info`, followed by three `foreach` loops that print the array, add up all of its elements, and add up only the even ones.

**Detailed breakdown:**

- **Creating the array:** `$info = array(5, -7, 12, 10, -7, 11, -6, 12, 1, -7, 2, 9);` stores 12 values in one variable, including both positive and negative numbers and some repeated values (`-7` appears three times and `12` appears twice). The rest of the assignment works with this same array.
- **Printing every element:** `foreach ($info as $all) { echo "$all, "; }` visits each value in order, using `$all` as the variable that holds the current element, and prints it followed by a comma and a space. After the loop, `echo "<br> <br>";` leaves a gap before the next result.
- **Calculating the total:** `$total = 0;` creates a running total, and `foreach ($info as $all) { $total += $all; }` adds each element to it. `echo "Total: $total";` prints the final sum, which for this array is `35`.
- **Calculating the total of even elements:** `$totalEven = 0;` starts a second running total, and inside the loop `if ($all % 2 == 0) { $totalEven += $all; }` only adds an element when dividing it by `2` leaves no remainder. The even elements in this array are `12`, `10`, `-6`, `12`, and `2`, so `"Total of even elements: 30"` is printed.

**Why this matters:** This establishes the core pattern used throughout the assignment — a `foreach` loop that walks through an array, combined with an accumulator variable (`$total`, `$totalEven`) and an `if` condition to decide which elements count.

---

## 2. `scr2.png` — Total of Odd Elements, Minimum, and Maximum

![Odd Total, Minimum, and Maximum Screenshot](scr2.png)

**What's in the image:** the continuation of the script — the total of the odd elements, followed by finding the smallest value in `$info` and the index (or indexes) where it appears, and then the same for the largest value.

**Detailed breakdown:**

- **Calculating the total of odd elements:** `$totalOdd = 0;` followed by `foreach ($info as $all) { if ($all % 2 != 0) { $totalOdd += $all; } }` mirrors the even-total loop, but with `!=` so only elements that leave a remainder when divided by `2` are added. The odd elements are `5`, `-7`, `-7`, `11`, `1`, `-7`, and `9`, so `"Total of odd elements: 5"` is printed (starting with a `<br>` so it appears on its own line after the even total). Together, the even total (`30`) and odd total (`5`) add up to the overall total of `35`.
- **Finding the minimum element:** `$min = $info[0];` assumes the first element is the smallest, then `for($i = 1; $i < count($info); $i++)` goes through the rest of the array, and `if ($info[$i] < $min) { $min = $info[$i]; }` replaces `$min` whenever a smaller value is found. `"Minimum elemnt is -7"` is printed.
- **Finding where the minimum is located:** a second loop, `for($i = 0; $i < count($info); $i++)`, checks every position with `if($info[$i] == $min)` and prints `"Minimum element is at index $i"` each time there's a match. Because `-7` appears three times, this prints three lines, for indexes `1`, `4`, and `9`.
- **Finding the maximum element:** the same pattern is used in reverse — `$max = $info[0];`, then `if($info[$i] > $max) { $max = $info[$i]; }` inside a `for` loop. `"Maximum element is 12"` is printed.
- **Finding where the maximum is located:** another loop checks `if($info[$i] == $max)` and prints `"Maximum element is at index: $i"`. Because `12` appears twice, this prints two lines, for indexes `2` and `7`.
- **A detail worth flagging:** the index loop for the minimum starts at `$i = 0`, but the index loop for the maximum starts at `$i = 1`, so index `0` is never checked when looking for the maximum. It doesn't change the output for this array (the first element, `5`, is not the maximum), but if the maximum were ever the first element, its index would be missed. Starting that loop at `0`, like the minimum one, would cover every position.

**Why this matters:** Finding a minimum or maximum by assuming the first element is the answer and then comparing against the rest is a standard array algorithm, and searching the array a second time to find *every* index where the value appears shows how repeated values need to be handled.

---

## 3. `scr3.png` — The `$colors` Array and the Start of the Colors Table

![Colors Array and Table Screenshot](scr3.png)

**What's in the image:** the closing brace of the last loop from the previous screenshot, the end of the first PHP block, and then a new PHP block that creates the two-dimensional `$colors` array and begins building an HTML table from it.

**Detailed breakdown:**

- **Closing the first block:** line `2` (`}`) closes the `for` loop that prints the maximum's index, and `?>` ends the first PHP block.
- **Creating a two-dimensional associative array:** `$colors` has three outer keys — `"Light"`, `"Normal"`, and `"Dark"` — and each one holds its own inner array with the keys `"Red"`, `"Green"`, and `"Blue"`. Each inner value is a text label such as `"Light Red"`, `"Normal Green"`, or `"Dark Blue"`, giving a 3 × 3 set of values.
- **Starting the table:** after `?>`, plain HTML takes over with `<table class="colors-table">`. The header row uses `<th>` cells: one empty `<th></th>` for the corner, then `Red`, `Green`, and `Blue` for the columns.
- **Looping over the rows:** `<?php foreach($colors as $row => $all) { ?>` opens a `foreach` that goes through the outer array. `$row` receives the key (`Light`, `Normal`, or `Dark`) and `$all` receives the inner array for that key.
- **Starting each table row:** inside the loop, `<tr>` opens a new row, `<td><?php echo $row; ?></td>` prints the row label, and `<td><?php echo $all["Red"]; ?></td>` prints the first color cell. The screenshot ends here, and the rest of the row continues in the next screenshot.

**Why this matters:** This is a first look at a nested array — an array whose values are themselves arrays — and at mixing PHP and HTML by closing and reopening `<?php ... ?>` tags so that the loop controls how many table rows are produced.

---

## 4. `scr4.png` — Finishing the Colors Table and Creating the `$classes` Array

![Colors Table End and Classes Array Screenshot](scr4.png)

**What's in the image:** the last two cells of each colors table row, the end of the table, and then a new PHP block that creates the `$classes` array and opens a second table.

**Detailed breakdown:**

- **Finishing each row:** `<td><?php echo $all["Green"]; ?></td>` and `<td><?php echo $all["Blue"]; ?></td>` complete the three color cells, and `</tr>` closes the row. `<?php } ?>` closes the `foreach`, so the full row is repeated once for `Light`, `Normal`, and `Dark`, and `</table>` ends the colors table.
- **Creating the `$classes` array:** a new PHP block starts with `echo "<br><br>";` for spacing and then builds `$classes`, another two-dimensional associative array. Its outer keys are the class codes `"CA221"`, `"CA233"`, and `"CA235"`, and each one holds an inner array with the keys `"Name"`, `"Phone"`, and `"Address"`.
- **Opening the second table:** after `?>`, `<table class="colors-table">` starts a new table, using the same `colors-table` class as the first one. The header row for this table continues in the next screenshot.

**Why this matters:** The `$classes` array has the same shape as `$colors` — an outer key that identifies a record and an inner array of named fields — which shows that the same nested-array pattern can hold different kinds of data, not just a grid of color labels.

---

## 5. `scr5.png` — The `$classes` Table

![Classes Table Screenshot](scr5.png)

**What's in the image:** the header row and the `foreach` loop that turn the `$classes` array into the second HTML table.

**Detailed breakdown:**

- **The header row:** `<th></th>` followed by `<th>CA221</th>`, `<th>CA233</th>`, and `<th>CA235</th>` — an empty corner cell and then the three class codes.
- **Looping over the records:** `<?php foreach($classes as $row => $all) { ?>` goes through the outer array, with `$row` holding the class code and `$all` holding that class's inner array.
- **Printing one row per class:** inside the loop, `<td><?php echo $row; ?></td>` prints the class code, and then `$all["Name"]`, `$all["Phone"]`, and `$all["Address"]` are printed in the next three cells. `<?php } ?>` closes the loop and `</table>` ends the table.
- **A detail worth flagging:** the header cells say `CA221`, `CA233`, and `CA235`, but the cells under them are filled with each class's **Name**, **Phone**, and **Address** (with the class code appearing as the first cell of each row). So the column headings don't describe what's actually in those columns. Compare this with the colors table, where the headings `Red`, `Green`, and `Blue` match the `$all["Red"]`, `$all["Green"]`, and `$all["Blue"]` cells below them. Using `Name`, `Phone`, and `Address` as the headings would match the data.

**Why this matters:** This repeats the `foreach ($array as $row => $all)` table pattern with a second data set, showing that the same loop structure can display any array whose records share the same inner keys — and it's a reminder that a table's headings should be matched to the columns that the loop actually produces.

---

## Concepts at a Glance

| Concept | Where It Appears | Key Idea |
|---|---|---|
| Creating an indexed array with `array(...)` | `scr1.png` | A single variable (`$info`) holds a list of values, including negatives and repeats |
| Looping through an array with `foreach` | `scr1.png`, `scr2.png` | `foreach ($info as $all)` visits every element in order |
| Running totals with `+=` | `scr1.png`, `scr2.png` | A variable starting at `0` accumulates the sum of all, even, or odd elements |
| Even/odd test with `%` | `scr1.png`, `scr2.png` | `% 2 == 0` selects even elements and `% 2 != 0` selects odd ones |
| Minimum and maximum search | `scr2.png` | Start with the first element as the answer, then compare it against the rest of the array |
| Finding every index of a value | `scr2.png` | A second loop with `count($info)` checks each position and prints every match |
| Two-dimensional associative arrays | `scr3.png`, `scr4.png` | Outer keys (`Light`, `CA221`, …) each hold an inner array of named values |
| `foreach ($array as $row => $all)` | `scr3.png`, `scr5.png` | Reads each outer key into `$row` and its inner array into `$all` |
| Mixing PHP and HTML for tables | `scr3.png`, `scr4.png`, `scr5.png` | Closing and reopening `<?php ... ?>` lets a loop generate repeated `<tr>` and `<td>` markup |

---

## Screenshot Folder Structure

```
Week4/
└── screenshots/
    ├── scr1.png
    ├── scr2.png
    ├── scr3.png
    ├── scr4.png
    └── scr5.png
```

Each screenshot above corresponds to its matching numbered section in this README, listed in the same order they appear in the **week4/screenshots** folder. The underlying source code these screenshots were captured from, `assigment.php`, lives in the parent `Week4` folder.
