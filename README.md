# Dynamic Website Deployment on AWS EC2

## Introduction

This project demonstrates the deployment of a dynamic website on AWS EC2 using Amazon Linux, Nginx, PHP, and MariaDB/MySQL. It includes a student registration form with a frontend built using HTML and CSS, a PHP backend for processing form submissions, and a relational database for storing student information.

## Objectives

- Deploy a dynamic website on an AWS EC2 instance.
- Configure Nginx as the web server.
- Create a responsive student registration form.
- Process form submissions using PHP.
- Configure MariaDB/MySQL for data storage.
- Verify submitted records in the database.

## Architecture

**Application Flow:**

<img width="1774" height="887" alt="image" src="https://github.com/user-attachments/assets/347a608a-e9aa-46f2-a989-e863ce92d27b" />


User / Browser → Internet → AWS EC2 Instance → Nginx → HTML/CSS Signup Form → PHP Backend → MariaDB/MySQL Database

The application runs on an Amazon Linux EC2 instance. Nginx serves the frontend, PHP processes form submissions, and MariaDB/MySQL stores the submitted information.



## Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud server hosting |
| Amazon Linux | Operating system |
| Nginx | Web server |
| HTML5 | Form structure |
| CSS3 | User interface styling |
| PHP | Backend form processing |
| MariaDB/MySQL | Relational database |
| Linux and systemd | Server configuration and service management |
| GitHub | Source code and project documentation |

## Deployment Steps

### 1. Connect to EC2

Connected to the Amazon Linux EC2 instance using SSH.

### 2. Update the System

```bash
sudo yum update
```

### 3. Install Required Packages

```bash
sudo yum install nginx mariadb105-server php -y
```

### 4. Start Services

```bash
sudo systemctl start nginx mariadb php-fpm
```

Enabled and checked the required services as part of the setup.

### 5. Create the Signup Form

Navigated to the Nginx document root:

```bash
cd /usr/share/nginx/html/
```

Created the frontend file:

```bash
sudo vim signup.html
```

Designed the student registration form using HTML and CSS.

### 6. Configure the Database

Opened the MySQL command line:

```bash
sudo mysql
```

Created the database and student table:

```sql
CREATE DATABASE FCT;
USE FCT;

CREATE TABLE student (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(20),
    email VARCHAR(300)
);
```

### 7. Configure the PHP Backend

Created the backend file:

```bash
sudo vim submit.php
```

Configured the PHP script to process signup form submissions and connect to the database.

### 8. Install the PHP Database Connector

```bash
sudo yum install php8.4-mysqlnd -y
```

### 9. Restart Services

```bash
sudo systemctl restart nginx mariadb php-fpm
```

### 10. Access and Test the Website

Accessed the website through the EC2 public IPv4 address:

**Public IP:** `184.73.103.148`

Opened the signup page in a browser, submitted the form, and checked the database to verify the stored records.

Website URL:

http://184.73.103.148/signup.html

## Screenshots


-Terminal:

<img width="1378" height="735" alt="Screenshot 2026-10-23 164725" src="https://github.com/user-attachments/assets/d4617a35-865e-46a1-8112-81ee6309b0a8" />

-Nginx, PHP-FPM status
<img width="1414" height="715" alt="Screenshot 2026-10-23 183026" src="https://github.com/user-attachments/assets/d75eca7b-612d-4dc0-b10e-875b305b02c4" />

-Database and table structure:

<img width="1031" height="602" alt="Screenshot 2026-10-23 165230" src="https://github.com/user-attachments/assets/1cdb0b70-e4cd-4515-a371-def81fc5e6b9" />

-Ec2 instance state:

<img width="1844" height="615" alt="Screenshot 2026-10-23 165345" src="https://github.com/user-attachments/assets/6601609f-353f-4d57-829d-b8ce7fc5d005" />

-Registration form interface:

<img width="1843" height="912" alt="Screenshot 2026-10-23 183612" src="https://github.com/user-attachments/assets/b5d9e4ed-2c5f-48f2-9499-a1cc002f8dcc" />

- Deployed and Verified database records:
- 
<img width="1231" height="420" alt="Screenshot 2026-10-23 183535" src="https://github.com/user-attachments/assets/44677058-39f8-4cfd-893b-62bb4643540b" />


## Key Learnings

- AWS EC2 provisioning and Linux server administration
- Nginx installation and configuration
- PHP backend development and form handling
- Relational database creation and management
- Frontend, backend, and database integration
- Testing form submissions and verifying stored records
- Documenting cloud deployment projects using GitHub

## Summary

Deployed and tested a dynamic student registration website on AWS EC2 using Nginx, PHP, and MariaDB/MySQL. The project demonstrates how a web form connects to a backend and relational database to process and store submitted information.

