# Web Application Development — PHP & MySQL

**Lecturer:** Yahye Ali Isse, MSc in Data Science

This repository contains coursework, labs, and projects for the **Web Application Development (PHP & MySQL)** course. It covers dynamic web development from first principles — PHP fundamentals, MySQL database design, and modern secure application practices — building up to a complete, deployed PHP/MySQL web application.

---

## Table of Contents

- [Course Objectives](#course-objectives)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Development Environment Setup](#development-environment-setup)
- [Repository Structure](#repository-structure)
- [Course Syllabus](#course-syllabus)
- [Textbook & References](#textbook--references)

---

## Course Objectives

By the end of this course, students will be able to:

- Understand web application development using PHP and MySQL
- Develop dynamic and interactive web applications with PHP
- Apply fundamental PHP programming concepts
- Develop and validate web forms
- Use jQuery, AJAX, and JSON for interactive applications
- Design databases and perform SQL operations using MySQL
- Develop secure PHP and MySQL CRUD applications
- Develop and consume RESTful APIs using PHP and JSON
- Implement sessions, authentication, authorization, and basic security
- Apply MVC and modern PHP application practices
- Apply fundamental Laravel concepts
- Design, develop, test, and present a complete PHP and MySQL web application

---

## Technologies Used

| Category | Tools |
|---|---|
| Markup / Styling | HTML, CSS |
| Scripting (server-side) | PHP |
| Scripting (client-side) | JavaScript, jQuery |
| Database | MySQL |
| Local Server Stack | XAMPP (Apache, MySQL, PHP, Perl) |
| Editor | Visual Studio Code |
| Version Control | Git & GitHub |
| Framework (later in course) | Laravel |

---

## Prerequisites

Before starting this course, you should already have:

- A basic understanding of HTML, especially HTML forms
- Basic programming knowledge (variables, conditionals, loops in any language)

---

## Development Environment Setup

This course uses **XAMPP** as the local development server (Apache + MySQL + PHP).

### 1. Install XAMPP

Download and install the latest version from [apachefriends.org](https://apachefriends.org/download.html).

- **XAMPP** — cross-platform (Windows, Linux, Mac)
- **WAMP** — Windows only (alternative, security-focused)

### 2. Understand the Document Root

The document root is the folder Apache serves when you visit `http://localhost`. By default, this is:

```
C:/xampp/htdocs
```

Any file or folder placed here is accessible via `http://localhost/...`. Note that `htdocs` itself never appears in the URL — it's treated as the root.

### 3. Test the Installation

1. Start **Apache** (and **MySQL**, if your work involves a database) from the XAMPP Control Panel.
2. Visit `http://localhost` or `http://127.0.0.1` in your browser.
3. If port `80` is already in use by another application (e.g. Skype), change Apache's port to `8080` in the XAMPP config, then access pages via `http://localhost:8080/...`.

### 4. Index Files

When a folder is requested without a specific filename (e.g. `http://localhost/test/`), the server automatically looks for a default **index** file — `index.php` takes priority over `index.html`. This means you don't need to include `index.php` in the URL to load it.

### 5. Troubleshooting: VMware Conflicts

If VMware is installed, its Authorization Service may already be bound to a port XAMPP needs (e.g. `443`). If Apache fails to start:

1. Open **Services** on your machine
2. Find **VMware Authorization Service**
3. Right-click → **Stop**

This won't cause issues with VMware itself, as long as you don't launch it while XAMPP's Apache server is running.

---

## Repository Structure

Coursework is organized by week, with each week's folder containing the PHP/HTML files written that week and a `Screenshot` subfolder documenting key code sections.

```
.
├── Week 1/
│   ├── index.php
│   ├── test.html
│   ├── README.md
│   └── Screenshot/
│       ├── 01-php-syntax.png
│       ├── 02-php-parameters.png
│       ├── 03-php-variables.png
│       ├── 04-php-strings.png
│       ├── 05-html-server-test.png
│       └── README.md
├── Week 2/
│   └── ...
└── README.md   ← this file
```

Each week folder includes its own `README.md` documenting that week's code, and each `Screenshot` subfolder includes its own `README.md` explaining what each captured screenshot demonstrates.

---

## Course Syllabus

| Chapter | Title | Key Topics |
|---|---|---|
| 1 | Introduction to PHP & MySQL | Course overview, HTTP/HTML basics, what PHP is and does, key PHP features, setting up a development server (XAMPP), document root, first PHP page |
| 2 | PHP Fundamentals & Control Structures | PHP syntax, `echo`/`print`, comments, variables and naming rules, data types, constants, operators, conditional statements (`if`, `switch`, ternary), loops (`while`, `do...while`, `for`), `break`/`continue`, nested loops |
| 3+ | *To be added as the course progresses* | Arrays, functions, form handling & validation, sessions & cookies, MySQL & database design, CRUD operations, AJAX/JSON, RESTful APIs, authentication & security, MVC, Laravel fundamentals |

### Chapter 1 — Introduction to PHP & MySQL

Covers what PHP is, how the client-server request/response cycle works, why PHP is used for dynamic web pages, and how to set up a local development environment with XAMPP. Concludes with writing and running a first PHP page (`index.php`) inside the XAMPP `htdocs` folder.

### Chapter 2 — PHP Fundamentals & Control Structures

Covers core PHP language mechanics: how `.php` files are structured and processed by the server, the difference between `echo` and `print`, single vs. double-quoted strings, commenting styles, variable rules, PHP's basic data types (integers, floats, strings, booleans), constants via `define()`, and the full range of PHP operators. The second half covers program flow — conditional structures (`if`, `if...else`, `if...elseif`, `switch`, the ternary `?` operator) and loop structures (`while`, `do...while`, `for`, nested loops, `break`, and `continue`).

---

## Textbook & References

- *Learning PHP, MySQL & JavaScript with jQuery, CSS & HTML5*, 6th Edition — Robin Nixon
- *PHP and MySQL for Dynamic Web Sites* — Larry Ullman
- PHP Manual — Stig Sæther Bakken
- [php.net](http://www.php.net)
- [w3schools.com](http://www.w3schools.com)
- [tutorialspoint.com](http://www.tutorialspoint.com)
- Lecturer's notes (in-class slides, per chapter)
