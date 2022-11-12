Intro to Windows
================

An introduction to Windows.

## 1. A little history

### (1)

_Read a little about Windows history and versions._

> N/A

### (2)

_When was Windows announced?_

> November 20, 1985

### (3)

_Which is the latest version of Windows?_

> Windows 11

### (4)

_Which is the latest version of Windows Server?_

>  Windows Server 2019

## 2. Windows file system and permissions explained

- Structure:
  - Logical Drives (Local Disk C:)
  - Folders
  - Files
- Important: `C:\`
  - `PerfLogs`              | system issues, performance reports
  - `Program Files [(x86)]` | program installation folders
  - `Users`                 | users and their data
  - `Windows`               | operating system, utility tools
- Permissions: user / group
  - Full control        | set ownership, permissions + modify files
  - Modify              | write + read + execute files
  - Read & execute      | read + execute files
  - List folder content
  - Read                | read files
  - Write               | write data to the folder
  - Special             | ?
- User, privileged user, administrator?
- `icacls <path>`
  - I, F, M, OI, IO, CI, RX, AD, WD: cryptic permissions
- `icacls <path> /setowner Users`
  - Who are "Users"? Some default group for non-administrators?

### (1)

_Read the above._

> N/A

### (2)

_In which folder are users profiles stored?_

> Users

## 2.  Understanding the authentication process

- LSA: Local Security Authority
  - Protected subsystem
  - Accounts, Security policies, Local security info
- Active Directory
  - AD: On-Premise
  - AAD: Azure
- Users -> (network logon) -> PCs, Servers + authorization
- On-Premise AD auth protocols:
  - NTLM:
    1. PC -> Server: negotiate auth
    2. Server -> PC: NTLM challenge
    3. PC -> Server: NTLM auth msg (response)
    4. Server -> AD: Netlogon info
    5. AD -> Server: Netlogon valid (auth OK)
    * Just auth: no integrity / confidentiality protection
  - LDAP / LDAPS:
    - +S: credentials are encrypted.
    - PC -> LDAP API -> Activate Direction Domain Controller (DC).
    - Credentials are sent via LDAP to DC for validation.
  - Kerberos:
    - Symmetric-key cryptography
    - Trusted third party authorization service (KDC)
    - Credential presented to service: session key
    - SPN: Service Principal Name
    - SPN determines the KDC of a resource
    - KDC: Key Distribution Center
    - TGT: authentication ticket
    - TGS: Ticket Granting Service
    - TGT encrypted with TGS secret key
    - Local session manager: detect expired session key
    - Key rotation: send current TGT, request new TGT, get new session key?
- Azure AD auth protocols:
  - Authentication store.
  - SAML:
    - Security Assertation Markup Language
    - SSO (Single Sign-On) standard
    - Service Provider (web app) trusts Identity Providers (auth service)
  - OAuth 2.0:
    - auth server: issues access tokens
    - resource owner: grants permissions associated with the access token
    - client: requests access token and passes it to resource server
    - resource server: application, that verifies access tokens
  - OpenID Connect (OIDC):
    - Adds auth to OAuth 2.0 (resource access & sharing)
    - Extra ID token (JWT: JSON Web Token)

### (1)

_Read the above._

> N/A

### (2)

_Which Active Directory is cloud based?_

> Azure Active Directory

### (3)

_Which authentication method does not provide data integrity?_

> NTLM

### (4)

_Which authentication method assigns a ticket in order for a user to login?_

> Kerberos

### (5)

_Which authentication method allow users to access applications with a single login (short name)?_

> SAML

### (6)

_Authentication method that uses JSON Web Tokens?_

> OpenID Connect

## 4. Utility tools

List of tools:
```
Task Scheduler, Event Viewer, Shared Folders, Local Users & Computers,
Performance Monitor, Disk Management, Services & Applications,
Local Security Policy, Disk Cleanup, Registry Editor,
CMD, PowerShell, Windows Terminal.
```

- Event Viewer: logs about system events.
- Windows registry database: OS and driver settings.
- `cd <REG DB>:\`, e.g. `HKLM:\`, `reg` to edit.
- Scripting: Batch and PowerShell.

### (1)

_Read the above._

> N/A

## 5. Types of servers

Domain Controller: AD/AAD infrastructure administration.

### (1)

_Read the above._

> N/A

### (2)

_Which can be considered the most important server?_

> Domain Controller

### (3)

_Which server can store emails?_

> Mail Server

## 6. Users and Groups Management

- OU: Organizational units.
- Why create "RDP Access" and "No RDP Access" groups?
- Why can you Grant and also Deny permissions?
- Groups can be nested.

### (1)

_Create the users and groups._

> N/A

## 7. Creating your first GPO

- GPO: Group Policy Object - e.g. User Rights Assignment.
- Local, site-wide, domain-level, organizational settings.
- Allow and Deny GPOs.
- GPO application (link): `gpupdate /force`.
- `whoami`
- UAC: User Access Control.

### (1)

_Create your first GPO._

> N/A
