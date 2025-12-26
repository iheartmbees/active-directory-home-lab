# Active Directory Home Lab – Windows Server 2022

## Project Overview

This project demonstrates the setup and configuration of a Windows Server 2022 Active Directory environment in a virtualized home lab. The lab includes installing Active Directory Domain Services (AD DS), configuring DNS, promoting a domain controller, designing Organizational Units (OUs), and managing users and computers according to best practices.

## Lab Objectives

- Build a virtualized Windows Server 2022 environment
- Configure static IP addressing and DNS
- Install and configure Active Directory Domain Services
- Promote a server to a Domain Controller
- Design a basic OU structure
- Create and manage domain users
- Verify AD functionality

## Environment & Tools

- Host OS: Windows 10/11
- Hypervisor: VMware Workstation
- Server OS: Windows Server 2022 (Evaluation)
- Hardware:
  - Processors: 2
  - RAM: 4 GB
  - Storage: 60 GB
- Networking: NAT (VMnet8)

![VM Setup](screenshots/vm-setup.png)

## Network Configuration

The server is configured with a static IPv4 address to ensure stability for Active Directory and DNS services. NAT networking allows internet access while maintaining isolation from the host network.

**Key settings:**

- Static IP assigned within NAT subnet
- DNS configured to point to the server itself
- Gateway set to VMware NAT gateway

![Network Configuration](screenshots/static-ip.png)

## Active Directory Installation

### Role Installation

- Installed Active Directory Domain Services using Server Manager
- Required features were added automatically by the wizard

![AD Installation Sucessful](screenshots/ad-install.png)

### Domain Controller Promotion

- Created a new forest
- Root domain name: `lab.local`
- Forest & Domain Functional Level: Windows Server 2016
- DNS Server and Global Catalog enabled
- DNS delegation not configured (not required in lab environment)
- Directory Services Restore Mode (DSRM) password set

![Domain Promotion](screenshots/domain-promotion.png)

## Organizational Unit (OU) Design

Custom OUs were created to allow Group Policy application and proper administration:

- LabUsers
- LabComputers

**Reasoning:** Default AD containers cannot receive Group Policy Objects (GPOs). Custom OUs allow policy application and proper management.

![Organisational Unit Structure](screenshots/ou-structure.png)

## User Management

- Created test domain users (Simbarashe Munyaradzi) and placed them in the LabUsers OU
- Built-in system accounts were left in default containers to avoid system issues

![Test User](screenshots/test-user.png)

## Verification & Testing

- Verified domain controller functionality via Active Directory Users and Computers
- Confirmed DNS resolution using `nslookup lab.local`
- Confirmed successful domain logon (`LAB\Administrator`)

![DNS Lookup](screenshots/ns-lookup.png)

![Successful Admin Domain Logon](screenshots/admin.png)

## Challenges & Solutions

- **Challenge:** Server Manager continued to show a static IP warning after configuration
- **Solution:** Confirmed static IP using `ipconfig /all`. Warning safely ignored as it did not affect AD functionality

## Verification and Testing – Domain-Joined Client

This section verifies that the Windows client machine was successfully joined to the `lab.local` Active Directory domain and can authenticate using a domain user account.

### Domain User Login Verification

The screenshot below shows a successful login to the Windows client using a domain user account. This confirms that Active Directory authentication, DNS resolution, and the trust relationship between the client and the domain controller are functioning correctly.

![Domain User Login](screenshots/domain-user-login.png)

### Client Computer Verification in Active Directory

The screenshot below confirms that the client computer object was automatically created in Active Directory and is visible within the appropriate Organizational Unit. This verifies that the domain controller recognizes and manages the client machine.

![Client Computer in ADUC](screenshots/client-computer-aduc.png)

## Group Policy Implementation and Verification

Group Policy Objects (GPOs) were configured to enforce centralized security controls across the Active Directory environment.

### Password Policy Configuration

A domain-wide password policy was implemented to enforce strong authentication requirements, including minimum password length and complexity.

![Password Policy](screenshots/password-policy.png)

### User Screen Lock Policy

A user-level Group Policy was created and linked to the `LabUsers` organizational unit to automatically lock user sessions after inactivity.

![Screen Lock Policy](screenshots/screen-lock-policy.png)

### Group Policy Verification

Group Policy application was verified on a domain-joined client using the `gpresult` command, confirming that the security policies were successfully applied.

![Group Policy Result](screenshots/gpresult.png)

## Skills Demonstrated

Skills Demonstrated

This project demonstrates hands-on experience with core enterprise IT and cybersecurity concepts through the design, deployment, and validation of a Windows Server Active Directory environment.

### Identity and Access Management

- Active Directory Domain Services (AD DS) deployment and configuration
- Domain Controller promotion and management
- Domain user and computer account administration
- Organizational Unit (OU) design and management

### Networking and DNS

- DNS configuration and dependency management for Active Directory
- Client DNS troubleshooting to resolve domain connectivity issues
- Domain controller discovery and name resolution verification

### Group Policy and Endpoint Security

- Group Policy Object (GPO) creation and linking
- User and computer policy configuration
- Password policy enforcement
- Screen lock and session security controls
- Policy application verification using gpresult and gpupdate

### Virtualization and Lab Design

- Virtual machine creation and management
- Network configuration for domain-based environments
- Client-to-server connectivity validation

### Troubleshooting and Diagnostics

- Active Directory connectivity troubleshooting
- Group Policy update failure analysis and resolution
- DNS and authentication issue diagnosis
- Service validation on the Domain Controller
