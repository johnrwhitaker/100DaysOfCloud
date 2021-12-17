**Add a cover photo like:**
![placeholder image](https://via.placeholder.com/1200x600)

# Implement Hybrid identity

## Cloud Research

Hybrid Identity is the process of connecting your on-premesis Active Directory with Azure Active Directory. This enables single sign-on for accessing both on-premesis and cloud based resources. This is done through Azure AD Connect. Azure AD Connect provides several features:

- **Password hash synchronization**
- **Pass-through authentication** allows the use of the same password on-premesis and in the cloud without the use of fedration
- **Federation integration** optional, but can be connected with an on-premesis AD FS infrastructure
- **Synchronization** creates users, groups and other objects and makes sure they are synched with the cloud
- **Health monitoring** allows you to view the health of your connection in the Azure portal

### Authentication

There are two options:

- **Cloud authentication** Azure AD handles authentication tasks using password hash synchronization and pass-through authentication
- **Federated authentication** Azure AD hands authentication off to a trusted authentication platform, like an on-premesis AD FS environment

### Password Hash Synchronization (PHS)

Synchs your on-premesis AD password hash with Azure AD so that you can use your on-premesis credentials with Azure services. This helps boost the productivity to users while also reducing help desk calls for password resets. The fewer passwords someone has to remember, the more likely they are to remember them.

The password hash is taken from the on-premesis AD environment, encrytped and then it is passed as a string to Azure AD. The string is then decrypted and stored as a user attribute for the user.

This is known as **same sign-on** instead of **single sign-on** since the user is still technically signing into two different resources (on-premesis and cloud) but with the same credentials

### Pass-Through Authentication (PTA)

Alternative to password hash syncronization. When a user signs in to Azure AD their credentials are validating directly with the on-premesis AD environment through a pass-through authentication agent. Usernames can be configured to use the on-premesis default username (userPrincipalName) or another attribute configured in Azure AD Connect. You can also install multiple agents to make sure that your that the environment that is servicing your sign-on requests is highly available.

### Federation with Azure AD

Federation is a collection of domains that have a trust relationship established. You can setup this kind of federation relationship between your on-premesis AD environment and Azure AD. This makes sure that all authentication tasks take place in your on-premesis environment and gives administrators more control over the environment.

If you implement this, you can still setup password hash synchronization as a backup in case the connection between the federated envionrment and Azure AD goes down.

### Password writeback

Password writeback allows for password changes in the cloud to be written back to the on-premesis AD environment in real time, while enforcing on-premesis password policies. This applies for both user and admin password changes in the cloud.

## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
