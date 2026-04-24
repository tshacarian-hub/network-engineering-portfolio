# Active Directory Home Lab

## Overview
Built a Windows Server Active Directory environment using VirtualBox.

## Objectives
- Install and configure AD DS
- Create domain users and groups
- Apply Group Policy
- Join client machine to domain
- Simulate IT support tasks

## Tools Used
- Windows Server 2025
- Windows 10
- Oracle VM VirtualBox

## Network Configuration
(Server IP, DNS settings here)

## Domain Setup
Domain: homelab.local

## User & Group Management
- Provisioned and managed user accounts within Active Directory.
- Structured users into departmental Organizational Units (IT and HR) for administrative control.
- Created and maintained security groups to streamline access management.
- Implemented role-based access control (RBAC) by assigning users to groups instead of direct permissions.
- Verified group membership and access rights to confirm proper permission inheritance.. 

## Group Policy
- Implemented Group Policy Objects (GPOs) to manage user and computer configurations.
- Linked GPOs to departmental OUs (IT and HR) for targeted policy enforcement.
- Configured security policies including password complexity, account restrictions, and user permissions.
- Restricted standard user capabilities (e.g., control panel access, system settings) while preserving administrative privileges.
- Validated GPO deployment using gpupdate /force and gpresult to confirm policy application.

## Client Machine Setup
- Provisioned a Windows client machine in the virtual lab environment.
- Assigned a static IP configuration to maintain reliable network connectivity.
- Successfully joined the client to the Active Directory domain.
- Verified domain communication and DNS resolution.
- Tested authentication with domain accounts to validate Group Policy and access control enforcement.

## IT Scenarios Tested
- Password reset
- Account unlock
- Folder permissions
- User disable

## Screenshots
<img width="1035" height="829" alt="IP didnt set the correct IP address" src="https://github.com/user-attachments/assets/8c21f507-4a41-4743-a83c-8d8303f89fb8" />
<img width="1030" height="859" alt="HR user" src="https://github.com/user-attachments/assets/d2615a7b-68bb-4ad7-a5d6-144cefb712e6" />
<img width="1026" height="859" alt="HR Team added" src="https://github.com/user-attachments/assets/4779037a-083c-4132-9e02-efaeaa475ddb" />
<img width="1024" height="855" alt="gpupdate result" src="https://github.com/user-attachments/assets/20cb4cfd-401c-463f-b7cf-e148591827a6" />
<img width="1017" height="845" alt="GPO linked to IT OU" src="https://github.com/user-attachments/assets/a698c09d-83f6-4635-a981-362340494d49" />
<img width="1021" height="853" alt="added user to IT Support" src="https://github.com/user-attachments/assets/c5ef4433-fe67-4eb6-83ab-df96df4d673a" />
<img width="1025" height="854" alt="added User to HR-Team" src="https://github.com/user-attachments/assets/708af132-69a9-4d9c-b945-ad208fd9e2de" />
<img width="1016" height="847" alt="AD DS role selected" src="https://github.com/user-attachments/assets/e7212f44-387e-4129-956e-ef5e125ebdc6" />
<img width="1023" height="848" alt="static IP setup" src="https://github.com/user-attachments/assets/23ee796a-1dda-4d6f-b488-2866b64c6d4c" />
<img width="1029" height="859" alt="Setup OU" src="https://github.com/user-attachments/assets/077470f9-eb11-4315-98d0-5cb44ed11a92" />
<img width="982" height="786" alt="Prohibit Access enable" src="https://github.com/user-attachments/assets/b6de4a0b-e4ef-41d4-9170-1c9fb9c9359f" />
<img width="1027" height="860" alt="new GPO created" src="https://github.com/user-attachments/assets/25884327-4dd4-40ec-9eb4-a74f58529cea" />
<img width="1027" height="861" alt="IT User" src="https://github.com/user-attachments/assets/00c58e62-c0d1-400e-a891-9bfb097f145d" />
<img width="1025" height="863" alt="IT Support added" src="https://github.com/user-attachments/assets/aade2799-40f3-42d0-81bf-6984b3fb97e7" />
<img width="1028" height="857" alt="IP set the correct IP Address" src="https://github.com/user-attachments/assets/dd5dbcb2-fd5d-4a66-844b-988cae7f4653" />

## What I Learned
- Active Directory structure
- User management
- Group Policy
- Domain environments

## Users, Groups, and Organizational Units

Created two Organizational Units (OUs) to organize users and groups by department:
- IT
- HR

Created the following users:
- JohnIT
- SarahHR
- AdminUser

Created the following security groups:
- IT-Support
- HR-Team

Added users to their department groups:
- JohnIT → IT-Support
- SarahHR → HR-Team

This step helped me learn how Active Directory organizes users and resources using OUs and security groups.

## Group Policy Configuration

Created a Group Policy Object (GPO) to restrict user access to the Control Panel.

Steps performed:
- Created a GPO named "Restrict-Control-Panel"
- Enabled setting: Prohibit access to Control Panel
- Linked the GPO to the IT Organizational Unit (OU)

Purpose:
This simulates real-world security controls where IT restricts user access to system settings.

Test:
Policy was applied using gpupdate /force and will be verified on a client machine.

