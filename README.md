<h1>Create Users and Security Groups</h1>

<h2>Tools and Software Used</h2>

- <b>Windows Server</b> 
- <b>Active Directory Users and Computers</b> 
- <b>PowerShell</b> 

<h2>Lab Description</h2>
  <p>This lab shows how to enable authorized users access to protected resources while denying access to unauthorized users. The first step in identifying a user is through a userame. The next step is to challenge the user by providing additional information such as a password or generated token value to prove that the supplied identity is authentic. Once the user has been authenticated, the next step is to see what permissions the user has. Permissions determine what the user can and cannot do. When a user requests access to a resource, the request is compared to the permissions list for that user which will determine if access will be granted or denied. This process is known as <b>access control</b>. Access controls protect resources from unauthorized access. This lab will utilize Active Directory to create several new users and groups. Folder structure will be created to align with the new groups and permissions will be assigned that will restrict user access to each folder based on group membership. Access will be verified by logging in as each user and attempting to access each folder. </p>
  
<h2>Directions</h2>
    <p>From the Windows Server taskbar, click <b>Server Manager</b> icon, to open the Server Manager application.</p>

![server manager icon](https://user-images.githubusercontent.com/107451613/177577215-136b235a-7600-40f6-a6bf-a7a5813decbc.png)

