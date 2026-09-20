# Week 2 — Code Screenshots

## Introduction

This README documents the screenshots inside the **Week 2 / Screenshot** directory for the **PHP & MySQL Course (CA233)**. Where Week 1 covered the basics of output, variables, and strings, Week 2 moves into control flow — constants, conditionals, switch statements, loops, and the ternary operator. Each screenshot isolates one of these topics from `test.php`, so each concept can be studied on its own before seeing how they combine in the full script.

The screenshots are ordered to match the sequence these topics appear in `test.php`, starting right after the `WEEK2` marker in the code: constants first, then the two flavors of conditional branching (`if`/`elseif`/`else` and `switch`), then the loop constructs (`while`, `do...while`, and `for`), the ternary operator, and finally nested loops.

| # | Filename | What It Covers |
|---|---|---|
| 1 | `const_screenshot.png` | Defining a constant and comparing a variable with `if`/`else` |
| 2 | `if.png` | Grading marks with `if`, `elseif`, and `else` |
| 3 | `switch statement.png` | Grading marks again, this time with a `switch` statement |
| 4 | `loop control.png` | Counting up to 5 with a `while` loop |
| 5 | `do while loop.png` | Running a loop body at least once with `do...while` |
| 6 | `ternary operator.png` | A one-line if/else using the ternary operator |
| 7 | `loop.png` | Building a 12-times table with a `for` loop |
| 8 | `nested loop.png` | A loop inside a loop, building a small multiplication table |

---

## 1. `const_screenshot.png` — Constants and a Simple Comparison

**What's in the image:** the `//CONSTANTS` block, where a fixed value is defined with `define()` and then a separate variable is checked against a threshold using `if`/`else`.

**Detailed breakdown:**

- **Creating a constant with `define()`:** `define("Age", 123);` creates a constant named `Age` with the value `123`. Unlike a variable, a constant is not prefixed with `$`, and once it's defined it cannot be reassigned anywhere later in the script. Constants are useful for values that should stay fixed for the life of the program — configuration values, fixed limits, and so on.
- **Reading a constant back out:** `echo Age;` prints the constant's value directly. Notice there's no `$` here either — referring to a constant uses its bare name, which is one of the clearest visual differences between a constant and a variable in PHP.
- **A variable comparison with `if`/`else`:** Separately, `$Age = 20;` declares an ordinary variable (note the `$`, and note that this is a different identifier from the constant `Age` above — PHP treats `Age` and `$Age` as completely unrelated). The following `if ($Age >= 18) echo "Adult "; else echo " Child ";` checks whether `$Age` meets or exceeds `18` and prints `"Adult "` if true, `" Child "` otherwise. Since `$Age` is `20`, the condition is true and `"Adult "` is printed.
- **Single-statement `if`/`else` without braces:** Both branches here are a single `echo` statement, so no `{ }` braces are used — PHP allows the braces to be omitted when a conditional branch is only one statement long, though it's common style to add them anyway once a project grows.

**Why this matters:** This screenshot introduces two separate ideas side by side — constants (fixed, non-reassignable values) and the most basic form of conditional logic (`if`/`else`) — setting up the vocabulary needed for the more detailed conditionals that follow.

---

## 2. `if.png` — Grading Marks with `if` / `elseif` / `else`

**What's in the image:** the `//if else statement` block, where a numeric mark is graded into a category using a chain of conditions.

**Detailed breakdown:**

- **Setting up the value to test:** `$marks = 87;` stores the score that will be evaluated against each condition in turn.
- **Chaining conditions with `elseif`:** The code checks conditions from most to least strict: `if($marks>=90)` for `"Excellent"`, then `elseif($marks>=80)` for `"very good"`, then `elseif($marks>=50)` for `"minimal pas"`, and finally `else` for `"fail"`. PHP evaluates each condition top to bottom and stops at the **first** one that's true — it never checks the remaining branches once a match is found.
- **Why the order of the conditions matters:** Because `87` satisfies both `>= 80` and `>= 50`, the order the branches are written in is what determines the result. Since `$marks >= 90` is checked first and fails, and `$marks >= 80` is checked next and succeeds, the output is `"very good"` — even though the later, looser condition (`>= 50`) would also have been true. If the conditions were written in the opposite order, the result would be wrong, since the first passing condition always wins.
- **The `else` as a catch-all:** If none of the `if`/`elseif` conditions match, the final `else` branch runs unconditionally, guaranteeing that some output is always produced no matter what value `$marks` holds.

**Why this matters:** This is the classic pattern for turning a continuous range of values (any mark from 0–100) into a small number of discrete categories, and it shows why condition order is a deliberate design choice, not an arbitrary one.

---

## 3. `switch statement.png` — Grading Marks Again, with `switch`

**What's in the image:** the `//Marks grade using switch` block, which re-solves the same kind of grading problem as the previous screenshot, but using a `switch` statement instead of `if`/`elseif`.

**Detailed breakdown:**

- **Setting up the value again:** `$marks = 100;` gives a fresh mark to grade, separate from the `87` used in the `if`/`elseif` example.
- **A `switch` built on boolean expressions, not fixed values:** A `switch` statement is normally used to compare a variable against a list of fixed values (`case 1:`, `case 2:`, etc.). This code instead writes full boolean expressions as the `case` labels — `case($marks >= 90):`, `case($marks >= 85):`, and so on. This works because PHP's `switch` actually compares the switched value (implicitly `true`, since none is given after `switch(...)`... more precisely here it's comparing `$marks` loosely against each `case` expression's result) using loose comparison, so a `case` that evaluates to a matching truthy/boolean result can be triggered. In practice, this produces the same top-to-bottom, "first match wins" behavior as the `if`/`elseif` chain above.
- **`break` after every case:** Each `case` ends with `break;`, which stops execution from continuing ("falling through") into the next `case` block. Without `break`, PHP would keep running the code in every subsequent case until it hit a `break` or the end of the `switch`, which is almost never the intended behavior.
- **The `default` case:** `default: echo "Fail"; break;` runs only if none of the `case` conditions match, serving the same role as the `else` in the previous screenshot's `if`/`elseif` chain.
- **Result for this run:** Since `$marks` is `100`, the very first case, `$marks >= 90`, is true, so `"A+"` is printed and the `break` exits the `switch` immediately.

**Why this matters:** Placing this right after the `if`/`elseif` version makes the comparison explicit — both blocks solve the same grading problem, showing two different tools that can express the same branching logic, with `switch` reading a little differently but still relying on the same "first match wins, then stop" behavior once conditions are involved.

---

## 4. `loop control.png` — Counting with a `while` Loop

**What's in the image:** the `// loop control` block, showing the most basic form of repetition in PHP — a `while` loop that counts from 1 to 5.

**Detailed breakdown:**

- **Initializing the counter:** `$count = 1;` sets up the variable that will be checked and updated on every pass through the loop.
- **The loop condition:** `while ($count <= 5) { ... }` re-checks its condition before every iteration. As long as `$count` is `5` or less, the loop body keeps running; the moment `$count` exceeds `5`, the loop stops.
- **What happens inside the loop:** `echo $count . "<br>";` prints the current value of `$count` followed by a line break, and `$count++;` increases `$count` by exactly `1` before the condition is checked again. This combination — print, then increment — is what produces the numbers 1 through 5, each on its own line.
- **Why the increment step is essential:** If `$count++;` were left out, `$count` would stay at `1` forever, the condition `$count <= 5` would never become false, and the loop would run infinitely. This is a common beginner bug worth calling out explicitly.

**Why this matters:** A `while` loop is the simplest way to repeat code an unknown or condition-based number of times, and this screenshot shows the three pieces every `while` loop needs: a starting value, a condition that eventually becomes false, and a step inside the loop that moves toward that false condition.

---

## 5. `do while loop.png` — Running the Loop Body at Least Once

**What's in the image:** the `// do while loop` block, which repeats the same 1-to-5 counting pattern as the previous screenshot, but restructured as a `do...while` loop.

**Detailed breakdown:**

- **Resetting the counter:** `$count = 1;` resets the same variable back to its starting point, independent of whatever value it held after the earlier `while` loop finished.
- **The key structural difference from `while`:** In a `do...while` loop, the loop body runs **first**, and the condition (`while ($count <= 5);`) is only checked **after** that first run completes. This guarantees the body executes at least once, even if the condition would have been false from the very start — a guarantee an ordinary `while` loop does not make, since it checks the condition before ever entering the body.
- **Same body, same output:** The body itself — `echo $count . "<br>"; $count++;` — is identical to the `while` loop version, so for this particular case (where `$count` starts at `1` and the condition is initially true anyway) the visible output ends up the same: the numbers 1 through 5.
- **Syntax note:** Unlike `while`, a `do...while` loop's condition line ends with a semicolon (`} while ($count <= 5);`), since the `while(...)` here is part of a single statement rather than the head of a new block.

**Why this matters:** Placing this right after the `while` loop makes the "check-first vs. check-last" distinction concrete — useful for situations where a loop body genuinely must run once regardless of the condition, such as showing a menu before asking whether to repeat it.

---

## 6. `ternary operator.png` — A One-Line Conditional

**What's in the image:** the `//Ternary Operators` block, showing how a simple `if`/`else` can be compressed into a single expression.

**Detailed breakdown:**

- **Setting up the value:** `$fuel = 0.5;` represents a fuel level, on some scale where `1` presumably means a full tank.
- **The ternary expression itself:** `$fuel <= 1 ? "Fill the tank now" : "There's enough fuel in the tank";` reads as "if `$fuel` is less than or equal to `1`, use the first string; otherwise use the second." The `?` marks the true branch and the `:` marks the false branch, all inside a single expression rather than a multi-line `if`/`else` block.
- **Feeding the result straight into `echo`:** Because a ternary expression evaluates to a value, `echo` can print that result directly — `echo $fuel <= 1 ? "..." : "...";` — without needing a temporary variable to hold the chosen string first.
- **Result for this run:** Since `$fuel` is `0.5`, which is indeed `<= 1`, the condition is true, so `"Fill the tank now"` is what gets printed.

**Why this matters:** The ternary operator is essentially shorthand for a two-branch `if`/`else` where each branch is a single value — useful for short, simple decisions where writing out a full `if`/`else` block would feel like more structure than the logic actually needs.

---

## 7. `loop.png` — Building a 12-Times Table with `for`

**What's in the image:** the `//loop` block, using a `for` loop to print the 12-times multiplication table from 1×12 up to 12×12.

**Detailed breakdown:**

- **The three parts of a `for` loop:** `for ($count = 1; $count <= 12; ++$count) { ... }` packs everything a loop needs into one line: `$count = 1` initializes the counter, `$count <= 12` is the condition checked before every iteration, and `++$count` increments the counter after every pass through the body. This is the same initialize/check/step pattern used in the `while` loop earlier, just written more compactly in a single statement.
- **Pre-increment (`++$count`) vs. post-increment (`$count++`):** This screenshot uses `++$count` (pre-increment) rather than the `$count++` (post-increment) style seen in the earlier `while` and `do...while` examples. In the context of a `for` loop's update clause, both forms have the same practical effect on the loop's behavior — the value is incremented by `1` either way — the difference between pre- and post-increment only matters when the result of the increment expression is used elsewhere in the same statement, which isn't the case here.
- **Building the output string:** `echo "$count times 12 is " . ($count * 12) . "<br>";` combines a string, a calculated value, and another string using the `.` concatenation operator. The parentheses around `$count * 12` ensure the multiplication happens before the result is concatenated into the surrounding text.

**Why this matters:** A `for` loop is the natural choice whenever the number of iterations is known in advance — here, exactly 12 lines are needed — which contrasts with the `while` loop pattern used earlier for open-ended, condition-driven repetition.

---

## 8. `nested loop.png` — A Loop Inside a Loop

**What's in the image:** the `//nested loops` block, where one `for` loop runs completely inside another, producing a small multiplication table.

**Detailed breakdown:**

- **The outer loop:** `for ($i = 1; $i <= 2; $i++) { ... }` runs exactly twice, with `$i` taking the values `1` and then `2`.
- **The inner loop:** Nested inside it, `for ($j = 1; $j <= 5; $j++) { ... }` runs completely from start to finish — all five of its iterations — for **each single pass** of the outer loop. This means the inner loop's full 1-through-5 cycle happens once while `$i` is `1`, and then happens again, independently, while `$i` is `2`.
- **Total number of iterations:** Since the outer loop runs 2 times and the inner loop runs 5 times for each of those, the innermost `echo` statement executes a total of `2 × 5 = 10` times.
- **Combining both counters in the output:** `echo "$i * $j = " . ($i * $j) . "<br>";` prints a line for every combination of `$i` and `$j`, showing the multiplication of the outer counter by the inner counter — effectively printing a compact two-row multiplication table (the 1-times and 2-times rows, each going up to 5).

**Why this matters:** Nesting loops is how grid-like or table-like patterns get generated — anywhere rows and columns, or two independent counters, need to be combined, an inner loop repeating fully inside an outer loop is the standard approach.

---

## Concepts at a Glance

| Concept | Where It Appears | Key Idea |
|---|---|---|
| `define()` | `const_screenshot.png` | Creates a constant that can't be reassigned later |
| `if` / `else` | `const_screenshot.png` | Basic two-branch conditional logic |
| `if` / `elseif` / `else` | `if.png` | Chained conditions checked top to bottom; first match wins |
| `switch` | `switch statement.png` | Alternative branching syntax, still "first match wins," needs `break` to avoid fall-through |
| `while` | `loop control.png` | Checks its condition before every iteration; may run zero times |
| `do...while` | `do while loop.png` | Checks its condition after the first run; always runs at least once |
| Ternary operator (`?:`) | `ternary operator.png` | Compresses a simple `if`/`else` into a single expression |
| `for` | `loop.png` | Best suited to a known, fixed number of iterations |
| Nested `for` loops | `nested loop.png` | An inner loop runs fully for every single pass of the outer loop |

---

## Screenshot Folder Structure

```
Week 2/
└── Screenshot/
    ├── const_screenshot.png
    ├── if.png
    ├── switch statement.png
    ├── loop control.png
    ├── do while loop.png
    ├── ternary operator.png
    ├── loop.png
    └── nested loop.png
```

Each screenshot above corresponds to its matching numbered section in this README, and the sections are ordered to match the sequence these topics appear in `test.php`. The underlying source file lives in the parent `Week 2` folder.
