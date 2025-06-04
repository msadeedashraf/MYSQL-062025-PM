
# MySQL Installation Guide

This document provides step-by-step instructions to install MySQL on **Windows** and **Oracle Linux 7.8 or above**.

---

## 🪟 MySQL Installation on Windows

### ✅ Step 1: Download MySQL Installer
1. Visit: https://dev.mysql.com/downloads/installer/
2. Choose between:
   - Web Installer (small download)
   - Full Installer (includes all components)
3. Click “Download” → “No thanks, just start my download” (optional login).

### ✅ Step 2: Run the Installer
- Double-click the `.msi` file.
- Allow permissions if prompted.

### ✅ Step 3: Choose Setup Type
Choose one of the following:
- Developer Default (recommended)
- Server Only
- Custom
- Full

Click **Next**.

### ✅ Step 4: Install Requirements
- Click **Execute** to install any missing dependencies.
- Click **Next**.

### ✅ Step 5: Install MySQL Products
- Click **Execute** to install selected features.
- Click **Next**.

### ✅ Step 6: Configure MySQL Server
- Choose Standalone MySQL Server.
- Config Type: Development Computer.
- Port: 3306 (default).
- Set root password.

### ✅ Step 7: Configure Windows Service
- Leave default service name (`MySQL80`).
- Enable “Start MySQL Server at System Startup”.

### ✅ Step 8: Apply Configuration
- Click **Execute** to apply all settings.
- Click **Finish**.

### ✅ Step 9: Test MySQL Server
- Launch MySQL Workbench.
- Connect to Local Instance with root password.

### ✅ Optional: Add MySQL to PATH (Command Line Use)
```bash
# Add this to PATH
C:\Program Files\MySQL\MySQL Server 8.0\bin
```
Open Command Prompt:
```bash
mysql -u root -p
```

---

## 🐧 MySQL Installation on Oracle Linux 7.8 or Above

### ✅ Step 1: Update the System
```bash
sudo yum update -y
```

### ✅ Step 2: Remove Old MySQL or MariaDB Versions
```bash
sudo yum remove mysql* mariadb* -y
```

### ✅ Step 3: Add the MySQL Yum Repository
```bash
wget https://dev.mysql.com/get/mysql80-community-release-el7-7.noarch.rpm
sudo rpm -Uvh mysql80-community-release-el7-7.noarch.rpm
yum repolist enabled | grep mysql
```

### ✅ Step 4: Install MySQL Server
```bash
sudo yum install mysql-server -y
```

### ✅ Step 5: Start and Enable MySQL
```bash
sudo systemctl start mysqld
sudo systemctl enable mysqld
```

### ✅ Step 6: Get the Temporary Root Password
```bash
sudo grep 'temporary password' /var/log/mysqld.log
```

### ✅ Step 7: Secure the Installation
```bash
sudo mysql_secure_installation
```

### ✅ Step 8: Verify MySQL Service Status
```bash
sudo systemctl status mysqld
```

### ✅ Step 9: Log In to MySQL
```bash
mysql -u root -p
```

### ✅ Optional: Open Firewall for MySQL
```bash
sudo firewall-cmd --permanent --zone=public --add-service=mysql
sudo firewall-cmd --reload
```

---

✅ MySQL is now ready to use!
