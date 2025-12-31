# 🎫Enterprise-Help-Desk-Lab-osTicket-🎟️
This project demonstrates the deployment and configuration of osTicket, an industry-standard open-source ticketing system. The goal was to simulate a corporate ITIL-aligned Service Desk environment by hosting a LAMP stack on a virtualized Linux server.
🛠️ Technology Stack
Virtualization: Oracle VM VirtualBox

Operating System: Ubuntu Server/Desktop 22.04 LTS

Web Server: Apache2

Database: MySQL

Language: PHP 8.x

Application: osTicket (Latest Stable Release)

🚀 Step-by-Step Implementation
Phase 1: Environment Setup
Created a New Virtual Machine in VirtualBox.

Allocated 2GB RAM and 20GB VDI Storage.

Set Network Adapter to Bridged Adapter to allow access from the host machine's browser.

Installed Ubuntu Server/Desktop(22.4 recommended) using the default Minimal installation.

Phase 2: Installing the LAMP(linux, apache, mysql, php) Stack
Installed the core web environment using the following Linux CLI commands:

Bash
# Update System
```
sudo apt update && sudo apt upgrade -y
```

# Install Apache, MySQL, and PHP extensions
```
sudo apt install apache2 mysql-server php php-mysql php-cgi php-fpm php-cli php-curl php-gd php-imap php-mbstring php-xml php-intl php-apcu -y
```
Phase 3: Database Configuration
Configured a secure MySQL backend for the ticketing data:

SQL
```
CREATE DATABASE osticket_db;
CREATE USER 'osticket_user'@'localhost' IDENTIFIED BY 'YourSecurePassword';
GRANT ALL PRIVILEGES ON osticket_db.* TO 'osticket_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(71).png)
Phase 4: osTicket Installation & Permissions
Downloaded the osTicket source files into /var/www/html/.

Created the ost-config.php file from the sample.

Critical Step: Adjusted file permissions to allow the webserver (www-data) to write to the configuration file:

Bash
```
sudo chown -R www-data:www-data /var/www/html/osticket
sudo chmod -R 755 /var/www/html/osticket
```
📋 Lab Simulations (Ticket Lifecycle)
1. User Portal: Submitting a Ticket
 
![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(76).png)

Scenario: A user cannot connect to the VPN for remote work.

Action: Used the Client Portal to open a "High Priority" ticket.

![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(79).png)
![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(80).png)
![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(82).png)


3. Agent Portal: Resolution & Knowledge Base


![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(78).png)
![image alt](https://github.com/gaganbisen08/Enterprise-Help-Desk-Lab-osTicket-/blob/main/Screenshot%20(82).png)


🧠 Key Skills Learned
Server Administration: Managing Linux services (Systemd) and troubleshooting web server logs.

Permission Management: Understanding the security implications of chmod and chown.

ITSM Framework: Understanding how Service Level Agreements (SLAs) impact business operations.

Network Troubleshooting: Configuring Bridged networking to communicate between Guest and Host OS.
