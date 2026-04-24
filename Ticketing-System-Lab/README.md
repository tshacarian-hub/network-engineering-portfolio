# Ticketing Systems Lab – osTicket on Windows Server (VirtualBox)

## Project Overview

This ticketing systems lab demonstrates how to build a fully functional help desk environment using:

* Windows Server 2022
* IIS (Internet Information Services)
* PHP
* MySQL
* osTicket

The goal of this project is to simulate a real-world IT support environment and gain hands-on experience with ticket management systems.

---

## Objectives

* Deploy a Windows Server environment in a virtual machine
* Configure IIS as a web server
* Install and configure PHP manually
* Install and configure MySQL
* Deploy osTicket as a help desk system
* Troubleshoot real-world setup issues
* Document all steps and errors

---

## Tools & Technologies

* Oracle VM VirtualBox
* Windows Server 2022 Standard (Desktop Experience)
* IIS (Web Server)
* PHP 8.x (Manual Install)
* MySQL Community Server
* osTicket (Open Source Ticketing System)

---

## Environment Setup

### Virtual Machine Configuration

* RAM: 4GB (minimum)
* CPU: 2 cores
* Storage: 60GB
* OS: Windows Server 2022 (Desktop Experience)

---

## IIS Installation

Installed IIS using PowerShell:

Install-WindowsFeature -name Web-Server -IncludeManagementTools
iisreset


Verified by accessing:

http://localhost

---

## MySQL Installation

* Installed MySQL Community Server (Server Only)
* Configured root account
* Created database:


CREATE DATABASE osticket;


---

## PHP Installation & Configuration

### Installation

* Downloaded PHP (Thread Safe ZIP)
* Extracted to:


C:\PHP


---

### php.ini Configuration

Enabled required extensions:


extension=gd
extension=intl
extension=mbstring
extension=mysqli
extension=pdo_mysql

<img width="1024" height="852" alt="php ini configuration" src="https://github.com/user-attachments/assets/77c0a75a-7f98-468e-8c3a-98fe2d21faf2" />

Set extension directory:


extension_dir = "C:\PHP\ext"

---

### IIS Integration (Manual)

Configured PHP using FastCGI:

* Opened IIS Manager
* Added Module Mapping:


Request path: *.php
Module: FastCgiModule
Executable: C:\PHP\php-cgi.exe
Name: PHP_via_FastCGI

<img width="1022" height="854" alt="Module Mapping" src="https://github.com/user-attachments/assets/167a6be5-9f61-447e-a9ea-4040e8933a58" />

Installed CGI feature:


Install-WindowsFeature Web-CGI
iisreset

<img width="1030" height="863" alt="web root setup" src="https://github.com/user-attachments/assets/956bbdf2-f96e-4e8c-a2b5-971a863d1c21" />
<img width="1026" height="856" alt="Screenshot 2026-04-15 023437" src="https://github.com/user-attachments/assets/23979795-34f6-4046-a9ac-5e7d822e068b" />


---

### Verification

Created test file:


<?php phpinfo(); ?>


Accessed:

http://localhost/info.php


Result: PHP successfully executed
<img width="1028" height="857" alt="php executed" src="https://github.com/user-attachments/assets/ffcd5704-6c31-4cc7-b8ce-a453a6a8ce6d" />

---

## Web Root Setup

All files placed in:


C:\inetpub\wwwroot


Created:

* test.html
* info.php

<img width="1030" height="863" alt="web root setup" src="https://github.com/user-attachments/assets/5235b68b-d533-4be3-acef-b083e87d7423" />

---

## Issues Encountered & Fixes

### Issue #1: VM Failed to Start
<img width="964" height="755" alt="Error-VM not starting" src="https://github.com/user-attachments/assets/59dbc9cf-c6bf-411c-9f00-e6be31edc8b9" />

* Cause: SVM (virtualization) disabled in BIOS
* Fix: Enabled SVM in BIOS
<img width="1180" height="883" alt="Error-Update SVM wasn&#39;t enable" src="https://github.com/user-attachments/assets/b80a4a13-f383-4e00-970c-3f45b30d4280" />

---

### Issue #2: Disk Partition Error
<img width="1032" height="856" alt="Error-Failed Disk Partiton" src="https://github.com/user-attachments/assets/ff4a8587-2497-4f0e-943d-aaf8892012ba" />

* Cause: Invalid partition
* Fix: Deleted and recreated partition
<img width="1022" height="859" alt="Error-Update Recreating the partition" src="https://github.com/user-attachments/assets/42eb78c1-ca89-4939-a831-49aecdf1b156" />

---

### Issue #3: Installed Server Core Instead of GUI
<img width="1044" height="881" alt="Screenshot 2026-04-14 213608" src="https://github.com/user-attachments/assets/9352563a-e22e-4ddf-b884-82a5251937af" />

* Cause: Wrong OS selection
* Fix: Reinstalled with Desktop Experience

<img width="1026" height="858" alt="Screenshot 2026-04-14 214715" src="https://github.com/user-attachments/assets/837be0e5-bc91-4c87-8ee6-cc98e1f2816b" />

---

### Issue #4: Windows License Terms Error
<img width="1016" height="849" alt="Screenshot 2026-04-14 214126" src="https://github.com/user-attachments/assets/5f2df87e-9ba2-4371-ae4a-299ac9f712f1" />

* Cause: Low RAM / ISO issue
* Fix: Increased RAM and reattached ISO

---

### Issue #5: Localhost Refused Connection
<img width="1027" height="852" alt="Screenshot 2026-04-14 220549" src="https://github.com/user-attachments/assets/26ad32b7-8dfa-4995-8dbb-72abe3b09fa1" />

* Cause: IIS not installed
* Fix: Installed IIS
<img width="1024" height="849" alt="Screenshot 2026-04-15 020639" src="https://github.com/user-attachments/assets/0315df1d-77ec-4bff-9e45-371d6543895a" />

---

### Issue #6: PHP Extensions Not Working

* Cause: Extensions disabled
* Fix: Enabled in php.ini

---

### Issue #7: Incorrect extension_dir

* Cause: Missing or incorrect path
* Fix: Set correct directory

---

### Issue #8: extension_dir Commented Out

* Cause: Semicolon disabled config
* Fix: Removed semicolon

---

### Issue #9: IIS 404 Error (info.php)

* Cause: File not found
* Fix: Created file in correct directory

---

### Issue #10: Files Not in Web Root

* Cause: Wrong file location
* Fix: Moved files to wwwroot

---

### Issue #11: File Extensions Hidden

* Cause: Windows hid extensions
* Fix: Enabled file extensions

---

### Issue #12: Files Saved as .txt

* Cause: Incorrect file type
* Fix: Renamed files properly

---

### Issue #13: PHP Not Executing

* Cause: PHP not registered in IIS
* Fix: Added FastCGI handler

---

### Issue #14: PHP Manager Download Failed

* Cause: Broken download link
* Fix: Configured PHP manually

---

### Issue #15: FastCGI Module Missing
<img width="1016" height="859" alt="Screenshot 2026-04-15 023132" src="https://github.com/user-attachments/assets/c2a9acba-e3da-467f-9f3e-b23333f1beeb" />

* Cause: CGI feature not installed
* Fix: Installed Web-CGI

---

### Issue #16: PowerShell Command Error

* Cause: Incorrect command syntax
* Fix: Corrected command and imported module

---

## Skills Gained

* Virtualization setup (VirtualBox)
* Windows Server administration
* IIS configuration
* PHP manual installation and configuration
* MySQL database setup
* Web server troubleshooting
* File system and permissions management
* Debugging real-world errors

---

## Next Steps

* Complete osTicket installation
* Configure departments and agents
* Simulate help desk tickets
* Document ticket workflows
* Add screenshots and diagrams
---

## Summary

This project demonstrates the ability to deploy and troubleshoot a full web-based ticketing system environment from scratch, using industry-relevant tools and configurations.

## Issue #17: MySQL Command Not Recognized

### What Happened
Running mysql -u root -p

 resulted in:
'mysql' is not recognized as an internal or external command

### When It Happened
After installing MySQL and attempting to access it via Command Prompt.

### Root Cause
MySQL was not added to the system PATH environment variable, so Windows could not locate the executable.

### Fix / Solution
1. Navigated to MySQL bin directory:
   C:\Program Files\MySQL\MySQL Server 9.6\bin
2. Successfully ran MySQL from that directory
3. Added the bin path to system PATH environment variable

### Result
MySQL command worked globally from any directory.

### What I Learned
- PATH variables allow system-wide command access
- Applications must be added to PATH for CLI usage
- Troubleshooting command recognition issues is a common IT task
<img width="988" height="545" alt="image_2026-04-15_074239239" src="https://github.com/user-attachments/assets/0344947d-c7f3-49b9-9fda-5c95af21c906" />
<img width="1016" height="801" alt="Screenshot 2026-04-19 230152" src="https://github.com/user-attachments/assets/ea6cdf0f-84ac-4d1e-9d91-442c371ab6df" />
