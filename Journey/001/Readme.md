![Day 1 title image](https://github.com/johnrwhitaker/100DaysOfCloud/blob/1750596a73bf1b2daaedacf836599ad3f9bfd2bb/Journey/001/Untitled.jpg)

# Secure Azure solutions with Azure Active Directory

## Introduction

I'm doing the Azure Security Engineer Challenge to kick off 100 Days of Cloud. Today focuses on using Azure Active Directory to secure your Azure solutions

## Prerequisite

None

## Cloud Research

Azure Active Directory is not simply a cloud version of Active Directory Domain Services. There are some core differences that are important to remember. 

- Azure AD is primarily an identity solution
- Azure AD does not use LDAP since it is HTTP/HTTPS. You use a REST API to query Azure AD
- It also does not use Kerberos authication, but uses HTTP/HTTPS solutions like SAML, WS-Federation and OpenID/OAuth
- Azure AD also uses a flat structure without Organization Units or Group Policy Objects

Azure AD is also a managed service, so you only need to worry about managing the users, groups, and policies and not the underlying infrastructure that it runs on.

### Roles

There are a wide variety of roles that can be assigned to users in Azure AD, each providing a variety of permissions to those users. 

One role that you should limit the use of in your Azure environment is the Global Administrator role. This role provides access to read and modify every administrative setting in your Azure AD organization. The person that signs up for an Azure subscription is assigned the Global Administrator role for the organization. The only people that can delegate administrator roles are Global Administrators and Privileged Role Administrators. Best practice recommendations are that you limit the number of users assigned the Global Administrator role to five.

Some other roles that can be assigned to help reduce the use of the Global Administrator role:

- **Application Administrator** - can create and manage all aspects of enterprise applications, application registrations, and application proxy settings
- **Application Developer** - can create application registrations when the "Users can register applications" setting is set to Yes
- **Authentication Administrator** - can set or reset non-password credentials for some users and can update passwords for all users
- **Azure DevOps Administrator** - can manage the Azure DevOps policy to restrict new Azure DevOps organization creation to a set of configurable users or groups
- **Azure Information Protection Administrator** - have all permissions in the Azure Information Protection service
- **B2C User Flow Administrator** - can create and manage B2C User Flows (also called "built-in" policies) in the Azure portal
- **B2C User Flow Attribute Administrator** - can add or delete custom attributes available to all user flows in the tenant
- **B2C IEF Keyset Administrator** - can create and manage policy keys and secrets for token encryption, token signatures, and claim encryption/decryption
- **B2C IEF Policy Administrator** - can create, read, update, and delete all custom policies in Azure AD B2C and therefore have full control over the Identity Experience Framework in the relevant Azure AD B2C tenant
- **Billing Administrator** - makes purchases, manages subscriptions, support tickets, and monitors servie health
- **Cloud Application Administrator** - same permissions as the Application Administrator role, excluding the ability to manage application proxy
- **Cloud Device Administrator** - can enable, disable, and delete devices in Azure AD and read Windows 10 BitLocker keys (if present) in the Azure portal
- **Compliance Administrator** - manage compliance-related features in the Microsoft 365 compliance center, Microsoft 365 admin center, Azure, and Microsoft 365 Security & Compliance Center
- **Comliance Data Administrator** - have permissions to track data in the Microsoft 365 compliance center, Microsoft 365 admin center, Azure and Exchange admin center
- **Conditional Access Administrator** - ability to manage Azure AD Conditional Access settings
- **Exchange Administrator** - have global permissions within Microsoft Exchange Online when the service is present
- **Directory Readers** - can read basic directory information
- **Global Administrator / Company Administrator** - access to all administrative features of Azure AD, all services that use Azure AD identities like Microsoft 365 security center, Microsoft 365 compliance center, Exchange Online, SharePoint Online, and Skype for Business Online
- **Groups Administrator** - can create/manage groups and its settings like naming and expiration policies
- **Seurity Administrator** - permissions to manage security-related features in the Microsoft 365 security center, Azure AD Identity Protection, Azure Information Protection, and Microsoft 365 Security & Compliance Center

### Azure AD Domain Services

If you need AD DS features like domain join, group policy, lightweight directory access protocol (LDAP), and Kerberos/NTLM authentication, then you can choose to deploy Azure AD domain services. These domain services can be deployed without the need to deploy, manage, and patch domain controllers. This can be used withthenants that are cloud-only, or ones that are synchronized with an on-premises AD DS environment.

In Azure AD DS LDAP write support is only supported for objects that are created in the Azure AD DS managed domain. It is not supported for objects that are synchronized. 

Azure AD DS is automatically synchronized with your Azure aD tenant. Objects created in Azure AD will be available in your Azure AD DS environment. This also includes users' passwords. Since Azure AD DS supports NTLM and Kerberos authentication you can deploy applications that rely on Windows-integrated authentication.

Azure AD DS also includes multiple domain controllers, which are distributed across zones in regions that support Azure Availability Zones, which allows Azure AD DS to be highly available.

### Create and manage Azure AD users

Every user that needs access to resources needs to have a user account. You can view user accounts by going to the **All users** blade.

![All users blade](https://github.com/johnrwhitaker/100DaysOfCloud/blob/ac8e851149488f1c8493815144945beb1d116786/Journey/001/5677D279-1AFE-47F7-BDD8-4C189EDC8F83.jpeg)

### Azure AD Groups

Azure AD allows for two different types of groups: Security groups and Microsoft 365 groups. Security groups are the most common and allow you to manage user and computer access to share resources. Microsoft 365 groups provide access to shared mailboxes, calendars, files, Sharepoint sites, and more.

There are multiple ways that Azure AD allows you to assign groups, which are reflected by the Membership Type field of the group. Assigned groups require you to manually add and remove users for them to have access to the group. Dynamic User groups let you use rules to define who should have access to the group. When a users properties match the rules then that user is added to the group. If a change is made that no longer matches the rules, then that user is dynamically removed from the group as well. There are also Dyname Device groups, which can only be a Security group. These work the same as Dynamic User groups, but for devices.

### Azure AD Administrative Units

Administrative units are Azure AD resources that can be a container for other Azure AD resources. Administrative units can only contain users and groups. Administrative Units allow you to restrict permissions in a role to any portion of your organization. You must have an Azure Active Directory Premium license in order to be able to use Administrative Units.

### Passwordless Authentication

Passwordless authentication allows you to sign in without having to use a password. The password is instead replaced with something you have plus something you are or something you know. 

There are several passwordless authentication methods:

- **Windows Hello for Business** - biometric and PIN credentials tied to a user's PC
- **FIDO2 Security Keys** - unphishable and stored on a USB stick
- **Microsoft Authenticator App** - used on iOS and Android devices, using matching number on the screen and then biometric (touch or face) or PIN to confirm
- **FIDO2 Smarcards** - uses FIDO2 keys in a smartcard format (in preview)
- **Temporary Access Pass** - time-limited passcode to set up security keys and Microsoft Authenticator (in preview)

## Next Steps

Tomorrow I will be looking at implementing hybrid identity.
Before taking my exam I will be taking a deeper dive into this topic

## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
