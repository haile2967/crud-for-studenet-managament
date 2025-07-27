Student Management System
A simple CRUD application built with Laravel 10.48.29, PHP 8.1.25, and SQLite to manage student records. Features include creating, viewing, updating, and deleting students with modals for user interaction, a unique serial number for each student, and edit/delete icons on the show page.
Features

Create Students: Add new students via a modal with fields for first name, middle name (optional), last name, section, and year/grade.
View Students: List all students in a table with serial numbers; view individual student details.
Update Students: Edit student details via a modal.
Delete Students: Delete students with a confirmation modal.
Serial Number: Automatically assigned unique serial number for each student.
Responsive UI: Built with Tailwind CSS and Heroicons for icons on the show page.
Database: Uses SQLite for lightweight storage.

Prerequisites

PHP: 8.1.25 or higher
Composer: Latest version
Node.js: For Tailwind CSS (optional, as CDN is used)
SQLite: Ensure SQLite3 is enabled in PHP (php_sqlite3.dll on Windows)
Git: For cloning the repository (optional)

Installation

Clone the Repository (if applicable):
git clone <repository-url>
cd crud-project


Install Dependencies:
composer install


Copy Environment File:
copy .env.example .env


Configure SQLite Database:

Ensure database/database.sqlite exists:type nul > database\database.sqlite


Update .env:DB_CONNECTION=sqlite
DB_DATABASE=C:\Users\haile\Downloads\LaravelCrud\crud-project\database\database.sqlite


Run Migrations:
php artisan migrate

Start Development Server:
php artisan serve


Access the application at http://127.0.0.1:8000.



Usage

Manage Students:

Create: Click "Create New Student" to open a modal. Enter details (e.g., First Name: Sarah, Last Name: Lee, Section: E, Year/Grade: 10) and save.
View: Click "View" in the table or visit /students/{id} to see details, including edit/delete icons.
Edit: Click "Edit" in the table or the pencil icon on the show page to open the edit modal.
Delete: Click "Delete" in the table or the cross icon on the show page to open the confirmation modal.


Serial Number:

Automatically assigned (e.g., 1, 2, 3...) upon student creation and displayed in the table and show page.



Project Structure

app/Models/Student.php: Eloquent model for students.
app/Http/Controllers/StudentController.php: Handles CRUD operations.
resources/views/layouts/app.blade.php: Base layout with Tailwind CSS and Heroicons.
resources/views/students/index.blade.php: Lists students with create/edit/delete modals.
resources/views/students/show.blade.php: Displays student details with edit/delete icons.
database/migrations/: Contains migrations for students table and serial_number.
routes/web.php: Defines routes for the application.
database/database.sqlite: SQLite database file.

Technologies

Laravel: 10.48.29
PHP: 8.1.25
SQLite: Database
Tailwind CSS: Styling (via CDN)
Heroicons: Icons for edit/delete (via CDN)
JavaScript: For modal interactivity

Testing

Start Server:
php artisan serve


Test CRUD:

Create: Add a student via the create modal at /students. Verify serial_number in the table.
Read: Check the table at /students and details at /students/{id}.
Update: Edit a student via the edit modal from the table or show page.
Delete: Delete a student via the delete modal from the table or show page.


Verify Database:
sqlite3 database\database.sqlite
.schema students


Expected schema:CREATE TABLE students (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    serial_number INTEGER UNIQUE,
    first_name VARCHAR(255) NOT NULL,
    middle_name VARCHAR(255),
    last_name VARCHAR(255) NOT NULL,
    section VARCHAR(255) NOT NULL,
    year_grade VARCHAR(255) NOT NULL,
    created_at DATETIME,
    updated_at DATETIME
);

License
This project is open-source and available under the MIT License.
