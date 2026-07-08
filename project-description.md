# Test Project Outline – Module B – Dynamic Website with Server-Side Rendering

## Competition time

3 hours

## Introduction

You must develop an admin panel for a classifieds service — a geek marketplace. This is the platform moderators' interface, where users can post and browse listings for LEGO sets, board games, books, souvenirs, and similar items.

In this module, you must implement management of adverts and their categories.

## General Description of Project and Tasks

The visual design is up to you, but UX will be assessed.

Example data files are provided under `assets/data/` (`users.csv`, `categories.csv`, `adverts.csv`). Advert images are available under `assets/images/`. Import all **CSV** files into your database. Use the moderator account from `users.csv` for testing (for example: Olivia Carter, `olivia@example.com`, `+44 7700 900321`).

In the project's `database` folder, save the database dump (`DB_DUMP.sql`) and the ER diagram (`ERD.png`).

The following website-wide requirements apply:

- Main content must be rendered on the server side. Client-side frameworks may be used for interactive elements (such as dropdowns), but the main content must work even with JavaScript disabled.
- Cross-site scripting (XSS) must be prevented: HTML entered in form fields must be displayed as text, not rendered as markup.
- SQL injection must be prevented: use ORM methods or prepared statements; do not concatenate user input into queries manually.

## Requirements

The following features must be implemented.

### Authentication

Only users with the `moderator` role can sign in to the admin panel.

The sign-in form contains login and password fields. The login field accepts either a **phone number** or **email**.

If the user is not authenticated, no other page must be accessible.

On successful authentication, the user is redirected to the admin panel home page.
If incorrect data is entered, an error message is displayed. The message must be the same for a non-existent username and an incorrect password.

### Header

The header must contain clickable links to the home page, categories list page, adverts list page, and users list page.

The header must be present on every page except the sign-in page.

### Home Page

The page must display the following data:

- Name of the currently authenticated user
- Number of adverts in each status at the current moment
- Number of users
- Top 10 adverts by views (only in `published` status), sorted by view count in descending order

### Categories Page

The page contains a list of categories (ID, name, number of adverts in `published` status) and an interface for adding, editing, and deleting categories (this may be implemented as modal windows or separate pages). Note that a category cannot be deleted if it has adverts linked to it in any status.

### Users Page

The page contains a list of users (ID, name, phone, email, number of adverts in `published` status).
The page must have one text field for searching by ID, phone number, and email at the same time (exact match).

### Adverts Page

The page contains a list of adverts and filters by status, category, and text. The text filter must search across the title, advert text, category name, and author name.
The adverts list must show a label for connected paid services, if any.

### Advert Details Page

The page contains the following data:

- ID, title, text, price, view count, category name, status, photo list (as a tile grid)
- ID, name, phone, and email of the author
- Interface for changing status
- Data on connected paid services, including expired ones (type, activation date, validity period)
- Ability to enable or disable a paid service for the advert

Allowed status transitions:

- `moderation` → `published`
- `moderation` → `declined`
- `published` → `declined`

### Export Adverts List

The adverts list page must have an export button. When clicked, the adverts list is exported to an `export_adverts.csv` file with the following columns:

- ID
- Title
- Category name
- Price
- Author phone number
- Author email
- Text
- Publication date

If **filters** are applied on the page, only the filtered records must be included in the export.

## Assessment

Module B will be assessed using the latest stable version of Google Chrome and Firefox. Server-side rendering, XSS and SQL injection protection, moderator authentication and access control, database operations, advert and category management, paid-service controls, CSV export, and overall UX are reviewed during evaluation. Database deliverables (`DB_DUMP.sql`, `ERD.png`) are checked for completeness and correct imported example data.

## Mark distribution

The table below outlines how marks are broken down and how they align with the WorldSkills Occupation Standards (WSOS). Please read the Technical Description for a full explanation of the WorldSkills Occupation Standards.

| WSOS SECTION | Description                            | Points |
| ------------ | -------------------------------------- | ------ |
| 1            | Work organization and management       | 0      |
| 2            | Communication and interpersonal skills | 0.5    |
| 3            | Design implementation                  | 0      |
| 4            | Front-end development                  | 0      |
| 5            | Back-end development                   | 21.5   |
| **Total**    |                                        | **22** |
