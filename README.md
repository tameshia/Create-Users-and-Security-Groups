<h1>Create Users and Security Groups</h1>

<h2>Tools and Software Used</h2>

- <b>Active Directory Users and Computers</b> 
- <b>PowerShell</b> 

<h2>Lab Description</h2>
  <p>This lab shows how to enable authorized users access to protected resources while denying access to unauthorized users. The first step in identifying a user is through a userame. The next step is to challenge the user by providing additional information such as a password or generated token value to prove that the supplied identity is authentic. Once the user has been authenticated, the next step is to see what permissions the user has. Permissions determine what the user can and cannot do. When a user requests access to a resource, the request is compared to the permissions list for that user which will determine if access will be granted or denied. This process is known as <b>access control</b>. Access controls protect resources from unauthorized access.</p>
  
  <p>A password policy may look something like this:
    <ol>
       <li>Passwords must be at least 9 characters in length and must contain 3 of the following: At least one upper case character, at least one numeric character, include at least one special character, [ e.g., ! @ # ? ] </li>
       <li>Users cannot use any of the previously used 10 passwords.</li>
       <li>Passwords must be changed every 90 days.</li>
       <li>User IDs and user names are not allowed</li>
    </ol>
    </hr>

  <h2>Directions</h2>
    <p>From the <b>Windows Start</b> icon, click on the <b>Server Manager</b> button. This will open the Server Manager application.</p>
