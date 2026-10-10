# Week 5 — Code Screenshots

## Introduction

This README documents the screenshots inside the **Week 5 / screenshots** directory for the **PHP & MySQL Course (CA233)**. Week 5 is about **HTML forms and processing form data with PHP**. The work builds a registration form (full name, password, sex, faculties, and comments) that is styled with CSS and sent to the same page using the `post` method. PHP then reads the submitted values from `$_POST` and prints them back on the page.

The code is one continuous file that mixes CSS, HTML, and PHP, and the four screenshots below are consecutive portions of it. Each screenshot is listed in the order it appears in the code (`code1.png` to `code4.png`).

| # | Filename | What It Covers |
|---|---|---|
| 1 | `code1.png` | The start of the `<style>` block: `body`, `.form-box`, text and password inputs, and `select` |
| 2 | `code2.png` | The rest of the CSS (`textarea`, submit and reset buttons), the closing of `<head>`, and the start of the form with the Full Name field |
| 3 | `code3.png` | The password field, the sex drop-down list, the faculties checkboxes, and the comments textarea |
| 4 | `code4.png` | The reset and submit buttons, the end of the form, and the PHP code that prints the submitted data |

---

## 1. `code1.png` — Styling the Page, the Form Box, and the Input Fields

![Body, Form Box, Inputs, and Select Styling Screenshot](code1.png)

**What's in the image:** the beginning of the `<style>` block, with the CSS rules for the page background, the white box that holds the form, the text and password inputs, and the drop-down list.

**Detailed breakdown:**

- **Styling the page:** the `body` rule uses `display: flex;`, `justify-content: center;`, and `align-items: center;` to place its content in the middle of the page. `min-height: 100vh;` makes the page at least as tall as the browser window, `margin: 0;` removes the default margin, and `background-color: #928585;` sets the page background.
- **Styling the form box:** the `.form-box` rule gives the box a `white` background, `padding: 30px;`, `width: 350px;`, rounded corners with `border-radius: 12px;`, and a soft shadow with `box-shadow: 0 4px 15px rgba(106, 92, 92, 0.2);`.
- **Styling text and password inputs:** one rule is shared by `input[type="text"]` and `input[type="password"]`. It sets `width: 100%;`, `padding: 10px;`, `margin-top: 5px;`, `box-sizing: border-box;` (so the padding does not make the field wider than the box), `border: 1px solid #ccc;`, and `border-radius: 6px;`.
- **Styling the drop-down list:** the `select` rule uses the same `width`, `padding`, `margin-top`, `border`, and `border-radius` values, so the drop-down list looks like the other fields.

**Why this matters:** Attribute selectors such as `input[type="text"]` let one rule style a specific kind of input, and listing two selectors separated by a comma lets them share the same styles.

---

## 2. `code2.png` — The Rest of the CSS and the Start of the Form

![Textarea and Button Styling, and the Start of the Form Screenshot](code2.png)

**What's in the image:** the remaining CSS rules, the end of the `<style>` block and the `<head>`, and then the start of the page body with the form and the Full Name field.

**Detailed breakdown:**

- **Styling the textarea:** the `textarea` rule sets `width: 100%;`, `height: 80px;`, `margin-top: 5px;`, `padding: 10px;`, `border: 1px solid #ccc;`, `border-radius: 6px;`, and `box-sizing: border-box;`.
- **Styling both buttons together:** `input[type="submit"], input[type="reset"]` shares `padding: 9px 18px;`, `border: none;`, `border-radius: 6px;`, and `cursor: pointer;`.
- **Styling each button separately:** the submit button gets `background-color: #2563eb;` and `color: white;`. The reset button gets `background-color: #e5e7eb;`, `color: #333;`, and `margin-right: 5px;` so there is a small gap between the two buttons.
- **Closing the head:** `</style>` ends the CSS and `</head>` ends the head section.
- **Starting the page body:** `<body>` opens the body, and `<div class="form-box">` creates the box that the `.form-box` CSS rule styles.
- **Starting the form:** `<form method="post">` opens the form and tells the browser to send the data with the `post` method. No `action` is given, so the form submits to the same page.
- **The Full Name field:** `<label for="fullname">Enter Full Name:</label>` is linked to `<input type="text" id="fullname" name="fullname">`. The `for` and `id` values match, and the `name` value, `fullname`, is the key PHP uses later to read the value. `<br><br>` adds spacing before the next field.

**Why this matters:** This is where the CSS ends and the form begins, and it introduces the connection between a label (`for`), an input (`id`), and the `name` attribute that becomes the key in `$_POST`.

---

## 3. `code3.png` — The Password, Sex, Faculties, and Comments Fields

![Password, Sex, Faculties, and Comments Fields Screenshot](code3.png)

**What's in the image:** the middle of the form — the password field, the sex drop-down list, the four faculty checkboxes, and the comments textarea.

**Detailed breakdown:**

- **The password field:** `<label for="password">Enter Password:</label>` is paired with `<input type="password" id="password" name="password">`. The `password` type hides the characters as they are typed.
- **The sex drop-down list:** `<label for="sex">Select Sex:</label>` is paired with `<select name="sex" id="sex">`. It has three options: the first has `value=""` and the text `Please select your sex`, and the other two have the values `Male` and `Female`. Because the first option's value is empty, choosing nothing submits an empty value.
- **The faculties checkboxes:** a plain `<label>Select Faculty:</label>` introduces four checkboxes. Each one is `<input type="checkbox" name="faculties[]" ...>` with its own value: `Computer Science`, `Business`, `Engineering`, and `Information Technology`. The text next to each checkbox is the visible label, and a `<br>` places each one on its own line.
- **Why `faculties[]` uses square brackets:** all four checkboxes share the same name, `faculties[]`, so PHP receives the checked ones together as an array.
- **The comments field:** `<label for="comments">Comments:</label>` is paired with `<textarea name="comments" id="comments"></textarea>`, followed by `<br><br>`.

**Why this matters:** This screenshot uses several different form controls — password input, drop-down list, checkboxes, and textarea — and shows how the `name` attribute decides how each value reaches PHP, including the array-style name used for checkboxes.

---

## 4. `code4.png` — Buttons, the End of the Form, and Processing the Data with PHP

![Buttons and PHP Form Processing Screenshot](code4.png)

**What's in the image:** the last two form buttons, the closing `</form>` tag, and the PHP block that reads `$_POST` and prints the submitted information.

**Detailed breakdown:**

- **The buttons:** `<input type="reset" value="Reset Form">` clears the form, and `<input type="submit" value="Register">` sends it. `</form>` then closes the form.
- **Checking that the form was submitted:** the PHP block starts with `if (!empty($_POST)) {`, so the printing code only runs when form data has been received.
- **Printing the sex:** `if (!empty($_POST['sex']))` prints `"Sex: "` followed by the chosen value. Otherwise the `else` branch prints `"Sex: please select your sex"`. `echo "<br>";` then moves to the next line.
- **Printing the full name, password, and comments:** each one uses `echo` with the label text joined to the `$_POST` value using the `.` operator — `$_POST["fullname"]`, `$_POST["password"]`, and `$_POST["comments"]` — followed by `echo "<br>";` so each appears on its own line.
- **Printing the faculties:** `if (!empty($_POST['faculties']))` checks that at least one checkbox was ticked, and `foreach ($_POST['faculties'] as $faculty)` goes through the array and prints `"Faculty: $faculty <br>"` for each selected faculty.
- **Closing the block:** `}` closes the main `if`, and `?>` ends the PHP block.
- **A detail worth flagging:** the password is printed back on the page exactly as it was typed. That is fine for practicing how `$_POST` works, but a real registration page should never display a password.
- **Another detail worth flagging:** the values from `$_POST` are printed directly, without being cleaned first (for example with `htmlspecialchars()`), so any HTML typed into a field would be treated as HTML by the browser.
- **One more detail:** only the sex field has an `else` message. If the user ticks no faculties, nothing is printed for that part and no message is shown.

**Why this matters:** This is where the form data is actually used. It shows the full flow — an HTML form sends data with `post`, and PHP checks with `!empty()` that it exists before reading it from `$_POST`, including looping over the array that the checkboxes produce.

---

## Concepts at a Glance

| Concept | Where It Appears | Key Idea |
|---|---|---|
| Centering with flexbox | `code1.png` | `display: flex;` with `justify-content` and `align-items` centers the form box on the page |
| Styling the form box | `code1.png` | `.form-box` uses padding, a fixed width, rounded corners, and a shadow |
| Attribute selectors | `code1.png`, `code2.png` | Selectors such as `input[type="text"]` style one kind of input, and a comma lets selectors share one rule |
| `box-sizing: border-box` | `code1.png`, `code2.png` | Keeps `width: 100%;` fields inside the form box even with padding and borders |
| Styling buttons | `code2.png` | Submit and reset share base styles and each gets its own colors |
| `<form method="post">` | `code2.png`, `code4.png` | Sends the form data with the `post` method to the same page |
| Label, `for`, `id`, and `name` | `code2.png`, `code3.png` | `for` matches `id` to link a label to its input, and `name` becomes the key in `$_POST` |
| Password input | `code3.png` | `type="password"` hides the typed characters |
| Drop-down list (`<select>`) | `code3.png` | An empty first option works as a "please select" prompt |
| Checkboxes with `faculties[]` | `code3.png`, `code4.png` | The `[]` in the name sends all ticked values to PHP as an array |
| Textarea | `code3.png` | A multi-line input for comments |
| `!empty($_POST)` and `!empty($_POST['key'])` | `code4.png` | Checks that data was submitted before reading and printing it |
| `if` / `else` | `code4.png` | Prints the sex if one was chosen, and a message if not |
| `foreach` over `$_POST['faculties']` | `code4.png` | Prints every selected faculty on its own line |
| Joining text with `.` | `code4.png` | `"Full Name: " . $_POST["fullname"]` combines a label and a value in one `echo` |

---

## Screenshot Folder Structure

```
Week5/
└── screenshots/
    ├── code1.png
    ├── code2.png
    ├── code3.png
    └── code4.png
```

Each screenshot above corresponds to its matching numbered section in this README, listed in the same order they appear in the code. The underlying source code these screenshots were captured from lives in the parent `Week5` folder.
