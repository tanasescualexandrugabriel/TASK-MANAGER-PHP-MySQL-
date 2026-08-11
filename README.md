TASK MANAGER (PHP + MySQL)
============================

WHAT MY PROJECT DOES
-----------------------
A simple web-based To-Do / Task Manager application. It lets a user:
- add a new task (title, description, due date)
- view the full list of tasks
- edit an existing task
- delete a task
- mark a task as "done" or "pending" with one click

It is built with plain PHP (no framework) and a MySQL database, using PDO
(PHP Data Objects) for a safe database connection that protects against
SQL injection.

This project is meant as a learning / portfolio project: it shows how to
connect PHP to MySQL, perform full CRUD (Create, Read, Update, Delete)
operations, and structure a small PHP project into clear, separate files.


HOW TO OPEN THE PROJECT
-------------------------
1. Unzip the project folder anywhere on your computer.
2. Open the folder "task-manager-php" in VS Code (File > Open Folder).
3. You will see the file structure described below. Open any .php file
   to read the code and comments.

To actually RUN the app (not required just to read the code), you need
a local server with PHP + MySQL, for example XAMPP, WAMP, or MAMP:
1. Import database.sql into MySQL (creates the database and sample data).
2. Edit config/database.php with your MySQL username/password.
3. Put the folder inside your server's web root (e.g. htdocs for XAMPP).
4. Open http://localhost/task-manager-php/ in your browser.


PROJECT STRUCTURE - WHAT EACH FILE DOES
------------------------------------------
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
task-manager-php/
|
|-- README.md
|       This file (project documentation).
|
|-- database.sql
|       SQL script that creates the database "task_manager" and the
|       "tasks" table, and inserts a few example tasks. Run this once
|       in MySQL (or import it via phpMyAdmin) before using the app.
|
|-- .gitignore
|       Tells Git which files/folders to ignore (OS files, IDE settings,
|       log files). Not code that runs, just a Git configuration file.
|
|-- config/
|   |-- database.php
|           Creates the PDO connection to the MySQL database. This is
|           the ONLY file where you need to change host/username/
|           password/database name. Every other PHP file includes this
|           file to get access to the database ($pdo variable).
|
|-- includes/
|   |-- header.php
|           The top part of every page: opens the <html> tag, loads the
|           CSS file, and shows the site title/navigation bar. Included
|           at the top of every page that shows something on screen.
|   |
|   |-- footer.php
|           The bottom part of every page: closes the <html> tags and
|           shows a small footer text. Included at the bottom of every
|           page.
|
|-- assets/
|   |-- style.css
|           All the visual styling (colors, spacing, table, buttons,
|           form fields). No logic here, just CSS.
|
|-- index.php
|       The HOME PAGE. Runs a SELECT query to get all tasks from the
|       database and displays them in a table, with buttons to edit,
|       delete, or toggle the status of each task.
|
|-- create.php
|       The "Add new task" page. Shows a form; when submitted, it
|       validates the input (title is required) and runs an INSERT
|       query to save the new task in the database.
|
|-- update.php
|       The "Edit task" page. Loads the existing task by its ID, shows
|       a pre-filled form, and on submit runs an UPDATE query to save
|       the changes.
|
|-- delete.php
|       Deletes one task by its ID (DELETE query), then redirects back
|       to index.php. No visible page, it just performs the action.
|
|-- toggle_status.php
|       Flips a task's status between "pending" and "done" with a
|       single click (UPDATE query), then redirects back to index.php.
|       No visible page, it just performs the action.

'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

HOW THE CODE FLOWS (SIMPLE VERSION)
--------------------------------------
1. User opens index.php -> sees the list of tasks.
2. User clicks "+ New task" -> goes to create.php -> fills form -> saves
   -> redirected back to index.php.
3. User clicks "Edit" on a task -> goes to update.php?id=X -> changes
   data -> saves -> redirected back to index.php.
4. User clicks "Delete" -> delete.php?id=X runs and redirects back.
5. User clicks "Mark as done" -> toggle_status.php?id=X runs and
   redirects back.

Every page that displays HTML (index.php, create.php, update.php)
includes header.php at the top and footer.php at the bottom, so the
page layout stays consistent everywhere.


TECHNOLOGIES USED
--------------------
- PHP (procedural style)
- MySQL (relational database)
- PDO with prepared statements (safe queries, no SQL injection)
- HTML + CSS (no JavaScript framework, no PHP framework)



