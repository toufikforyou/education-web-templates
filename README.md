<div align="center">

# 🏫 Infancy Academy School

**The website and admin panel for Infancy Academy School, Parulkandi, Kazipur, Sirajganj.**

Parents apply for admission online, students check their results from home, and the school runs it all from one admin panel.

[![PHP](https://img.shields.io/badge/PHP-mysqli-777BB4?logo=php&logoColor=white)](#run-it-locally)
[![MySQL](https://img.shields.io/badge/MySQL-MariaDB-4479A1?logo=mysql&logoColor=white)](#run-it-locally)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-4-7952B3?logo=bootstrap&logoColor=white)](#how-its-built)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

</div>

---

## Why it exists

A small school in a rural upazila still runs on paper: admission forms handed in at the office, results pinned
to a notice board, and parents travelling in just to check either one.

This site moves those everyday jobs online. It was built for a real school, so the pages are in Bangla and
English, and everything is kept simple enough for the school's own staff to run.

## What it does

**For parents and students**

- **Online admission:** fill in a new-student registration form and get a confirmation once it's submitted.
- **Result lookup:** enter class, roll number and exam to see a student's result, with GPA.
- **Find a registration:** look up an application that was already sent.
- **Student and teacher logins,** plus teacher registration.
- **Contact form** for questions to the school.

**For the school (admin panel)**

- **Dashboard** to manage the whole site from one place.
- **Posts:** publish, edit and remove the notices and news shown on the website.
- **Users and admins:** register users, edit accounts and profiles, and add or remove admins.
- **Account security:** change password, and reset a forgotten password with a one-time code sent by SMS.

## How it's built

A classic PHP site, made to run on cheap shared hosting with no build step:

| | |
|---|---|
| **Backend** | Plain PHP with `mysqli` |
| **Database** | MySQL / MariaDB (database name `ias`) |
| **Frontend** | HTML, CSS, Bootstrap 4, Font Awesome, jQuery |
| **SMS** | GreenWeb SMS API for one-time codes |

```text
/                     public site: home, admission, results, contact, logins
├── admin/            admin panel: dashboard, posts, users, admins, OTP reset
├── teacher/          teacher area
├── css/  js/         site styles and scripts
├── ias_image/        site images
├── student_images/   uploaded student photos
└── db_conn.php       database connection (admin/db_conn.php for the panel)
```

## Run it locally

You'll need PHP, MySQL or MariaDB, and a web server. [XAMPP](https://www.apachefriends.org/) gives you all three in one install.

1. Clone the repo into your web root (for XAMPP, that's `htdocs`):

   ```bash
   git clone https://github.com/toufikforyou/infancy-academy-school-website.git
   ```

2. Create a database called `ias` in phpMyAdmin.
3. Check the connection settings in `db_conn.php` and `admin/db_conn.php`. They default to `localhost`, user `root`, no password.
4. Open <http://localhost/infancy-academy-school-website/>.

> **The database schema isn't in this repo yet.** The code expects tables such as `admin_info`, `user_info`,
> `post_info`, `new_student`, `infancystudent` and `result`. A SQL dump will be added so a fresh install works out of the box.

## Known limitations

This was built a while ago, and a few things would be done differently today:

- Passwords are hashed with MD5. They should move to PHP's `password_hash()` and `password_verify()`.
- Queries are built by hand. Prepared statements would make them safer.
- Settings such as the database login and SMS credentials live in the PHP files. They belong in an environment file that isn't committed.

If you'd like to help with any of these, pull requests are welcome.

## Author

Built by **MH TOUFIK** · [@toufikforyou](https://github.com/toufikforyou) · [toufikforyou.dev](https://www.toufikforyou.dev)

## License

Released under the [MIT License](LICENSE).
