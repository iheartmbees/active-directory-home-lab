# Active Directory Home Lab – Windows Server 2022

## Project Overview
<<<<<<< HEAD

This project demonstrates the setup and configuration of a Windows Server 2022 Active Directory environment in a virtualized home lab. The lab includes installing Active Directory Domain Services (AD DS), configuring DNS, promoting a domain controller, designing Organizational Units (OUs), and managing users and computers according to best practices.

## Lab Objectives

=======
This project demonstrates the setup and configuration of a Windows Server 2022 Active Directory environment in a virtualized home lab. The lab includes installing Active Directory Domain Services (AD DS), configuring DNS, promoting a domain controller, designing Organizational Units (OUs), and managing users and computers according to best practices.

## Lab Objectives
>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
- Build a virtualized Windows Server 2022 environment
- Configure static IP addressing and DNS
- Install and configure Active Directory Domain Services
- Promote a server to a Domain Controller
- Design a basic OU structure
- Create and manage domain users
- Verify AD functionality

## Environment & Tools
<<<<<<< HEAD

=======
>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
- Host OS: Windows 10/11
- Hypervisor: VMware Workstation
- Server OS: Windows Server 2022 (Evaluation)
- Hardware:
  - CPU: Intel Core i7 (11th Gen)
  - RAM: 16 GB
  - Storage: 1 TB SSD
- Networking: NAT (VMnet8)

## Network Configuration
<<<<<<< HEAD

The server is configured with a static IPv4 address to ensure stability for Active Directory and DNS services. NAT networking allows internet access while maintaining isolation from the host network.

**Key settings:**

=======
The server is configured with a static IPv4 address to ensure stability for Active Directory and DNS services. NAT networking allows internet access while maintaining isolation from the host network.

**Key settings:**
>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
- Static IP assigned within NAT subnet
- DNS configured to point to the server itself
- Gateway set to VMware NAT gateway

## Active Directory Installation
<<<<<<< HEAD

### Role Installation

=======
### Role Installation
>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
- Installed Active Directory Domain Services using Server Manager
- Required features were added automatically by the wizard

### Domain Controller Promotion
<<<<<<< HEAD

=======
>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
- Created a new forest
- Root domain name: `lab.local`
- Forest & Domain Functional Level: Windows Server 2022
- DNS Server and Global Catalog enabled
- DNS delegation not configured (not required in lab environment)
- Directory Services Restore Mode (DSRM) password set

## Organizational Unit (OU) Design
<<<<<<< HEAD

Custom OUs were created to allow Group Policy application and proper administration:
=======
Custom OUs were created to allow Group Policy application and proper administration:

>>>>>>> 915940d894c6a5d97fefcb916d374b1d1e3c7be0
