<div align="center">

<br/>

```text
 _    _           _            ______ _ _   
| |  | |         | |          |  ____(_) |  
| |__| |_   _  __| |_ __ __ _| |__   _| |_ 
|  __  | | | |/ _` | '__/ _` |  __| | | __|
| |  | | |_| | (_| | | | (_| | |    | | |_ 
|_|  |_|\__, |\__,_|_|  \__,_|_|    |_|\__|
          __/ |                              
         |___/                               
```

# 🏋️ HydraFit

### *From Fat To Fit — Health & Weight Management Platform*

[![PHP](https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![CSS3](https://img.shields.io/badge/CSS3-Vanilla-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.x-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)](https://www.chartjs.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

</div>

---

## 📖 Table of Contents

- [About HydraFit](#-about-hydrafit)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [System Requirements](#-system-requirements)
- [Installation Guide](#-installation-guide)
- [Database Configuration](#-database-configuration)
- [Email Configuration (PHPMailer)](#-email-configuration-phpmailer)
- [ImgBB Configuration (Photo Upload)](#-imgbb-configuration-photo-upload)
- [User Flow](#-user-flow)
- [API Endpoints](#-api-endpoints)
- [Admin Panel](#-admin-panel)
- [Security](#-security)
- [Contributors](#-contributors)

---

## 🌟 About HydraFit

**HydraFit** is a PHP & MySQL-based health management web application that helps users monitor and manage their fitness journey — from daily weight tracking and real-time BMI calculation to accessing an interactive workout library.

> *"We Help You Go From Fat To Fit"*

This application is designed with a **multi-role** approach (User & Admin), features a 3-step onboarding system, and integrates various modern libraries such as Chart.js for weight data visualization, SweetAlert2 for interactive notifications, and PHPMailer for OTP password reset email services.

---

## ✨ Key Features

### 👤 User Features

| Feature | Description |
|-------|-----------|
| 🔐 **Registration & Login** | Register with a username/email, login with either. Passwords are hashed using BCrypt. |
| 📋 **3-Step Onboarding** | Step-by-step profile setup flow: (1) Register → (2) Name → (3) Physical Data. |
| 📊 **Weight Tracker** | Input daily weight, visualized with interactive line charts (1W / 1M / ALL). |
| 🧮 **BMI Calculator** | Automatic and real-time BMI calculation every time the weight is updated. |
| 📚 **Course Library** | Access the workout library with real-time search capabilities. |
| 💪 **Workout Detail** | View detailed exercise movements complete with animated GIFs and instructions. |
| ⚙️ **Account Settings** | Edit profile, change photo (upload to ImgBB), change password, delete account. |
| 🔑 **Forgot Password** | Reset password via a 6-digit OTP sent to email (valid for 5 minutes). |
| 🚪 **Auto-Logout** | The session is automatically cleared when navigating to the login page while already logged in. |

### 🛡️ Admin Features

| Feature | Description |
|-------|-----------|
| 📊 **Admin Dashboard** | Quick statistics: total users, total admins, total active courses. |
| 📝 **Manage Courses** | Full CRUD for course data (title, tagline, thumbnail, banner, target muscle). |
| 💪 **Manage Exercises** | CRUD for exercise movements per course (name, duration/reps, GIF URL, instructions). |
| 👥 **Manage Users** | View all users, change roles (User/Admin), delete user accounts. |
| 👑 **Super Admin** | Super Admin account protection — cannot be modified/deleted by regular admins. |
| 🔒 **Role-Based Access** | Automatic routing: Admin → `admin/dashboard.php`, User → `welcome.php`. |

---

## 🛠 Tech Stack

### Backend
- **PHP 8.x** — Server-side logic, session management, prepared statements
- **MySQL / MariaDB** — Relational database
- **PHPMailer** — Sending OTP emails via Gmail SMTP
- **ImgBB API** — Cloud image hosting for user profile photos

### Frontend
- **HTML5** — Semantic page structure
- **Vanilla CSS3** — Fully custom styling without a framework
- **Vanilla JavaScript (ES6+)** — Fetch API, async/await, DOM manipulation
- **Google Fonts (Poppins)** — Modern typography
- **Chart.js** — Interactive weight chart visualization
- **SweetAlert2** — Elegant dialogs/notifications

### Tools & Library
- **Canvas API** — Interactive particle animation on the landing page
- **LocalStorage API** — Saving the sidebar collapse state

---

## 📁 Project Structure

```
HydraFit_Project/
│
├── 📄 index.php                  # Landing page (Hero + Particle animation)
├── 📄 login.php                  # Login page
├── 📄 register.php               # Registration page
├── 📄 logout.php                 # Logout handler (clears session)
│
├── 📄 create-profile.php         # Onboarding Step 2 — Enter name
├── 📄 complete-profile.php       # Onboarding Step 3 — Physical data (Height, Weight, etc.)
├── 📄 welcome.php                # Welcome page after setup is complete
│
├── 📄 dashboard.php              # Main user dashboard (chart, BMI, stats)
├── 📄 course.php                 # Workout course library
├── 📄 workout_detail.php         # Movement details within a course
├── 📄 settings.php               # User account settings
│
├── 📄 forgot_password.php        # Email input form for password reset
├── 📄 verify_otp.php             # Form to verify the 6-digit OTP code
├── 📄 reset_password.php         # New password input form
├── 📄 send_otp.php               # PHPMailer logic — send OTP email
│
├── 📄 api_weight.php             # REST API — GET & POST weight data
├── 📄 api_settings.php           # REST API — Update profile, change password, delete account
│
├── 📄 koneksi.php                # MySQL database connection configuration
│
├── 📁 admin/                     # Admin Panel (restricted access: role='admin')
│   ├── 📄 dashboard.php          # Admin dashboard — global statistics
│   ├── 📄 manage_course.php      # CRUD course data
│   ├── 📄 manage_exercises.php   # CRUD exercise movements per course
│   ├── 📄 manage_users.php       # User & role management
│   └── 📄 logout.php             # Admin logout
│
├── 📁 assets/
│   ├── 📁 css/
│   │   ├── style.css             # Global CSS & Landing Page
│   │   ├── onboarding.css        # CSS for Auth & Onboarding forms
│   │   ├── dashboard.css         # CSS for Dashboard, Sidebar, Cards
│   │   ├── course.css            # CSS for Course Library & Workout Detail
│   │   ├── settings.css          # CSS for Settings Page
│   │   ├── welcome.css           # CSS for Welcome Page
│   │   ├── admin.css             # Specific CSS for Admin Panel
│   │   ├── manage_users.css      # CSS for Manage Users table
│   │   └── auth_style.css        # CSS for Forgot/Reset Password pages
│   │
│   ├── 📁 js/
│   │   ├── script.js             # Landing page JS (particles, modals, navigation)
│   │   ├── dashboard.js          # Dashboard JS (Chart.js, Weight API, Search)
│   │   ├── settings.js           # Settings JS (AJAX profile, password, delete)
│   │   ├── toggle_password.js    # JS to toggle show/hide password
│   │   ├── onboarding.js         # Onboarding form JS
│   │   ├── manage_users.js       # Admin JS — confirm user deletion
│   │   ├── auth_validation.js    # Auth form validation JS
│   │   └── welcome.js            # Welcome page JS
│   │
│   └── 📁 image/
│       ├── Fit.jpg               # Hero section image
│       └── google.png            # Other image assets
│
└── 📁 PHPMailer-master/          # PHPMailer library for OTP emails
    └── src/
        ├── PHPMailer.php
        ├── SMTP.php
        └── Exception.php
```

---

## 💻 System Requirements

Before installation, ensure your environment meets the following requirements:

| Component | Minimum Version | Description |
|----------|--------------|------------|
| **PHP** | 7.4+ (Recommended 8.x) | With `mysqli`, `curl`, `openssl` extensions enabled |
| **MySQL** | 5.7+ / MariaDB 10.3+ | Relational database |
| **Web Server** | Apache / Nginx | Recommended: Apache with XAMPP/Laragon |
| **Browser** | Chrome 90+ / Firefox 88+ | For Canvas & ES6 features |
| **Internet Connection** | Optional | Required for Google Fonts, Chart.js CDN, SweetAlert2, and ImgBB |

> 💡 **Recommendation**: Use **XAMPP** (Windows) or **Laragon** for the easiest local setup.

---

## 🚀 Installation Guide

### Step 1: Clone / Download Project

```bash
# Clone using Git
git clone https://github.com/YosuaSurianto/HydraFit.git

# Or download the ZIP, then extract it
```

### Step 2: Move to Web Server Directory

```
# For XAMPP (Windows)
C:\xampp\htdocs\HydraFit_Project\

# For Laragon (Windows)
C:\laragon\www\HydraFit_Project\

# For Linux (Apache)
/var/www/html/HydraFit_Project/
```

### Step 3: Create & Import Database

1. Open **phpMyAdmin** (usually at `http://localhost/phpmyadmin`)
2. Create a new database named `db_hydrafit`
3. Import the following SQL schema:

```sql
-- ============================================================
-- DATABASE: db_hydrafit
-- ============================================================

CREATE DATABASE IF NOT EXISTS `db_hydrafit`
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_unicode_ci;

USE `db_hydrafit`;

-- ============================================================
-- TABLE: users
-- ============================================================
CREATE TABLE `users` (
  `id`             INT(11)      NOT NULL AUTO_INCREMENT,
  `username`       VARCHAR(50)  NOT NULL,
  `email`          VARCHAR(100) NOT NULL UNIQUE,
  `password`       VARCHAR(255) NOT NULL,
  `role`           ENUM('user','admin') NOT NULL DEFAULT 'user',
  `first_name`     VARCHAR(50)  DEFAULT NULL,
  `last_name`      VARCHAR(50)  DEFAULT NULL,
  `birth_date`     DATE         DEFAULT NULL,
  `gender`         ENUM('Male','Female') DEFAULT NULL,
  `blood_type`     ENUM('A','B','AB','O') DEFAULT NULL,
  `height`         FLOAT        DEFAULT NULL COMMENT 'in cm',
  `current_weight` FLOAT        DEFAULT NULL COMMENT 'in kg',
  `target_weight`  FLOAT        DEFAULT NULL COMMENT 'in kg',
  `avatar`         TEXT         DEFAULT NULL COMMENT 'Photo URL from ImgBB',
  `otp_code`       VARCHAR(10)  DEFAULT NULL,
  `otp_expiry`     DATETIME     DEFAULT NULL,
  `created_at`     TIMESTAMP    NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ============================================================
-- TABLE: weight_tracking
-- ============================================================
CREATE TABLE `weight_tracking` (
  `id`          INT(11)   NOT NULL AUTO_INCREMENT,
  `user_id`     INT(11)   NOT NULL,
  `weight`      FLOAT     NOT NULL COMMENT 'in kg',
  `recorded_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  CONSTRAINT `fk_weight_user`
    FOREIGN KEY (`user_id`) REFERENCES `users`(`id`)
    ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ============================================================
-- TABLE: courses
-- ============================================================
CREATE TABLE `courses` (
  `id`            INT(11)      NOT NULL AUTO_INCREMENT,
  `title`         VARCHAR(150) NOT NULL,
  `tagline`       VARCHAR(255) DEFAULT NULL COMMENT 'Short course slogan',
  `description`   TEXT         DEFAULT NULL,
  `thumbnail`     TEXT         DEFAULT NULL COMMENT 'Card image URL (16:9 ratio)',
  `banner`        TEXT         DEFAULT NULL COMMENT 'Wide header image URL',
  `target_muscle` VARCHAR(100) DEFAULT NULL,
  `created_at`    TIMESTAMP    NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ============================================================
-- TABLE: exercises
-- ============================================================
CREATE TABLE `exercises` (
  `id`          INT(11)      NOT NULL AUTO_INCREMENT,
  `course_id`   INT(11)      NOT NULL,
  `name`        VARCHAR(150) NOT NULL,
  `duration`    VARCHAR(100) DEFAULT NULL COMMENT 'Example: 30 Seconds / 15 Reps',
  `instruction` TEXT         DEFAULT NULL,
  `gif_image`   TEXT         DEFAULT NULL COMMENT 'Movement animation GIF URL',
  PRIMARY KEY (`id`),
  CONSTRAINT `fk_exercise_course`
    FOREIGN KEY (`course_id`) REFERENCES `courses`(`id`)
    ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ============================================================
-- SEED: Default Admin Account
-- Password: admin123 (BCrypt hash)
-- ============================================================
INSERT INTO `users` (`username`, `email`, `password`, `role`, `first_name`)
VALUES (
  'superadmin',
  'admin@hydrafit.com',
  '$2y$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC/.og/at2.uheWG/igi',
  'admin',
  'Admin'
);
```

> ⚠️ **Note**: The password hash above is for `password` (plain text). Replace it with a hash you generate yourself using `password_hash('yourpassword', PASSWORD_DEFAULT)` in PHP.

### Step 4: Database Connection Configuration

Open the [`koneksi.php`](koneksi.php) file and adjust the configuration:

```php
<?php
$host = "localhost";      // Database host (usually localhost)
$user = "root";           // Database username
$pass = "";               // Database password (empty if XAMPP default)
$db   = "db_hydrafit";    // Database name

$conn = mysqli_connect($host, $user, $pass, $db);

if (!$conn) {
    die("Connection Failed: " . mysqli_connect_error());
}
?>
```

### Step 5: Run the Application

Open your browser and access:

```
http://localhost/HydraFit_Project/
```

---

## 📧 Email Configuration (PHPMailer)

HydraFit uses **PHPMailer** via Gmail SMTP for the password reset feature with OTP.

Open the [`send_otp.php`](send_otp.php) file and change the following configuration:

```php
$mail->Username   = 'youremail@gmail.com';   // Replace with your Gmail address
$mail->Password   = 'xxxx xxxx xxxx xxxx';   // Gmail App Password (not your regular password!)
$mail->setFrom('no-reply@hydrafit.com', 'HydraFit Support');
```

### How to Get a Gmail App Password:

1. Go to **Google Account Settings** → **Security**
2. Enable **2-Step Verification** (required)
3. Search for **App passwords** → Generate a new password
4. Select App: **Mail** | Device: **Other (Custom name)** → Type "HydraFit"
5. Copy the 16 characters that appear → paste into `$mail->Password`

> 🔐 **Important**: Do not commit your App Password to a public repository. Use environment variables or a `.env` file for production.

---

## 🖼 ImgBB Configuration (Photo Upload)

User profile photos are uploaded to **ImgBB** (a free image hosting service).

Open the [`api_settings.php`](api_settings.php) file and replace the API Key:

```php
// Around line 43
$api_key = 'YOUR_API_KEY_HERE';
```

### How to Get an ImgBB API Key:

1. Register/login at [https://imgbb.com](https://imgbb.com)
2. Go to [https://api.imgbb.com](https://api.imgbb.com)
3. Click **Get API Key** → Copy the provided API key
4. Paste it into the `$api_key` variable in `api_settings.php`

---

## 🗺 User Flow

### Registration & Onboarding Flow

```
Landing Page (index.php)
    │
    ├──[Click "Sign Up"]──► register.php
    │                           │
    │                    [Enter username, email, password]
    │                           │
    │                           ▼
    │                    create-profile.php  ◄── Step 2 of 3
    │                           │
    │                    [Enter first name & last name]
    │                           │
    │                           ▼
    │                    complete-profile.php ◄── Step 3 of 3
    │                           │
    │                    [Enter birth date, gender,
    │                     blood type, height, weight]
    │                           │
    │                           ▼
    │                    welcome.php ──► dashboard.php
    │
    └──[Click "Login"]───► login.php
                               │
                        [Admin] ──► admin/dashboard.php
                        [User]  ──► welcome.php ──► dashboard.php
```

### Password Reset Flow

```
login.php
    │
    [Click "Forgot Password?"]
    │
    ▼
forgot_password.php
    │
    [Enter email → Server sends OTP via Gmail SMTP]
    │
    ▼
verify_otp.php
    │
    [Enter 6-digit OTP (valid for 5 mins)]
    │
    ▼
reset_password.php
    │
    [Enter new password → Password hashed with BCrypt → Saved]
    │
    ▼
login.php  ✅
```

### Weight Update Flow (AJAX)

```
dashboard.php
    │
    [User types a number → Clicks "Update Weight"]
    │
    ▼ [Fetch POST]
api_weight.php
    │
    [INSERT to weight_tracking + UPDATE current_weight in users]
    [CALCULATE new BMI]
    │
    ▼ [JSON Response]
dashboard.js
    │
    [Update UI: Weight card, BMI card, Refresh Chart]
```

---

## 🔌 API Endpoints

HydraFit has two internal API files that are consumed via AJAX by the frontend JavaScript.

### `api_weight.php`

| Method | Parameter | Description | Response |
|--------|-----------|-----------|----------|
| `GET` | `?range=1W` | Fetch weight data for the last 1 week (20 entries) | `{status, data[{label, value}]}` |
| `GET` | `?range=1M` | Fetch weight data for the last 1 month (60 entries) | `{status, data[{label, value}]}` |
| `GET` | `?range=ALL` | Fetch all weight data (500 entries) | `{status, data[{label, value}]}` |
| `POST` | `{weight: float}` | Save new body weight & calculate BMI | `{status, message, new_bmi: {score, status, color}}` |

> **Auth**: All endpoints require an active login session (`$_SESSION['user_id']`).

---

### `api_settings.php`

| Method | Action | Parameter | Description |
|--------|--------|-----------|-----------|
| `POST` | `update_profile` | `first_name, last_name, username, height, target_weight, avatar (optional file)` | Update profile data + upload photo to ImgBB |
| `POST` | `change_password` | `current_password, new_password` | Verify old password → hash & save new password |
| `POST` | `delete_account` | _(none)_ | Delete all user data + weight tracking, destroy session |

---

## 🖥 Admin Panel

### Accessing the Admin Panel

1. Log in using an account with `role = 'admin'`
2. The system automatically redirects to `admin/dashboard.php`
3. Or access it directly: `http://localhost/HydraFit_Project/admin/dashboard.php`

### Creating a New Course

1. Go to **Admin Panel → Manage Courses**
2. Fill out the form: **Course Title**, **Tagline**, **Target Muscle**, **Thumbnail URL**, **Banner URL** (optional), **Description**
3. Click **"Save New Course"**

> 💡 **Tip**: Use image URLs from Google Images, Unsplash, or other hosting. The ideal thumbnail uses a **16:9** ratio.

### Adding Exercises

1. In the Course Library table, click the **"Exercises"** button on the desired course
2. Fill out the form: **Exercise Name**, **Duration/Reps** (e.g., `30 Seconds` or `15 Reps`), **GIF/Image URL**, **Instructions**
3. Click **"Add Exercise"**

> 💡 **Tip**: Use animated movement GIFs from [Giphy](https://giphy.com) or other sources for a better user experience.

### Managing Users

1. Go to **Admin Panel → Manage Users**
2. Change the user's role using the **User/Admin** dropdown (auto-submits)
3. Delete a user with the **Delete** button (with a SweetAlert confirmation)

> 🛡️ **Super Admin Protection**: Accounts listed in the `$super_admins` array in `manage_users.php` cannot be modified or deleted by any admin.

```php
// admin/manage_users.php — Lines 17-19
$super_admins = [
    'superadminemail@gmail.com', // Add Super Admin email here
];
```

---

## 🔒 Security

HydraFit implements various layers of security:

| Mechanism | Implementation | Location |
|-----------|-------------|--------|
| **Password Hashing** | BCrypt via `password_hash()` & `password_verify()` | `register.php`, `api_settings.php` |
| **SQL Injection Prevention** | Prepared Statements (`mysqli->prepare()`, `bind_param()`) | All PHP files that query the database |
| **Session Security** | `session_regenerate_id(true)` after successful login | `login.php` |
| **XSS Prevention** | `htmlspecialchars()` on all data output to HTML | All view files |
| **Role-Based Access Control** | Checking `$_SESSION['role']` on every admin page | `admin/*.php` |
| **Auth Guard** | Redirect to login if the session does not exist | All protected pages |
| **OTP Expiry** | Password reset OTP expires in **5 minutes** | `forgot_password.php`, `verify_otp.php` |
| **Super Admin Protection** | Whitelisted Super Admin emails cannot be modified | `admin/manage_users.php` |
| **Self-Action Prevention** | Admins cannot delete/change the role of their own account | `admin/manage_users.php` |
| **File Upload Validation** | File type & size validation (max 2MB, JPG/PNG) | `settings.js`, `api_settings.php` |

> ⚠️ **Note for Production**: Some code sections still use `mysqli_real_escape_string()` (instead of Prepared Statements). It is recommended to fully migrate to Prepared Statements before deploying to a production environment.

---

## 📐 Database Schema

```
┌─────────────────────────────────────────────────────────────────────────┐
│                              USERS                                       │
│  id │ username │ email │ password │ role │ first_name │ last_name │ ... │
│  PK │          │ UNIQUE│ BCrypt   │ ENUM │            │           │     │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │ id = user_id (FK)
                    ┌──────────────┘
                    │
        ┌───────────▼─────────────┐
        │    WEIGHT_TRACKING      │
        │  id │ user_id │ weight  │
        │  PK │ FK(users)│ FLOAT  │
        │     │ CASCADE  │        │
        └─────────────────────────┘

┌──────────────────────────────────────────────┐
│                   COURSES                    │
│  id │ title │ tagline │ thumbnail │ banner │ │
│  PK │       │         │  URL      │  URL   │ │
└────────────────────────┬─────────────────────┘
                         │ id = course_id (FK)
              ┌──────────┘
              │
   ┌──────────▼──────────────────────────────┐
   │              EXERCISES                  │
   │  id │ course_id │ name │ duration │ gif │
   │  PK │ FK(courses)│      │          │ URL │
   │     │ CASCADE   │      │          │     │
   └─────────────────────────────────────────┘
```

---

## 🎨 Design & UI

HydraFit uses a modern design with the following concepts:

- **Primary Color**: Blue (`#2563eb`) — main actions and branding
- **Accent Color**: Cyan (`#06b6d4`) — welcomes, highlights
- **Success Color**: Green (`#22c55e`) — Normal BMI, confirmations
- **Warning Color**: Orange (`#f97316`) — Overweight BMI
- **Danger Color**: Red (`#ef4444`) — Obese BMI, delete account
- **Font**: **Poppins** (Google Fonts) — Modern, clean, easy to read
- **Animations**: Interactive canvas particles on the landing page, fade-in transitions, smooth sidebar collapse
- **Components**: Glassmorphism-like cards, collapsible navigation sidebar, interactive charts

---

## 📌 Development Notes

- This project was built as a **learning project** for pure PHP web development (native PHP, no framework).
- It does not use Composer — all libraries are included manually (PHPMailer is copied directly).
- It does not use a `.env` file — sensitive configurations are directly in the PHP files (adjust for production).
- Routing is handled **manually** using PHP's `header("Location: ...")`.

---

## 👨‍💻 Contributors

<table>
  <tr>
    <td align="center">
      <b>Yosua Surianto</b><br/>
      <sub>FullStack Developer</sub><br/>
      <a href="https://www.instagram.com/dracoo.88/">📸 Instagram</a> •
      <a href="https://x.com/Dracoo72">🐦 Twitter/X</a>
    </td>
  </tr>
</table>

---

## 📄 License

This project is released under the **MIT** license. You are free to use, modify, and distribute this project provided that you include attribution to the original creator.

---

<div align="center">

**Made with ❤️ by [Yosua Surianto](https://www.instagram.com/dracoo.88/)**

*"The only bad workout is the one that didn't happen."*

</div>
