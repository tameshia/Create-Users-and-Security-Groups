<h1>Create Users and Security Groups</h1>

<h2>Tools and Software Used</h2>

- <b>Windows Server</b> 
- <b>Active Directory Users and Computers</b> 
- <b>PowerShell</b> 

<h2>Lab Description</h2>
  <p>This lab shows how to enable authorized users access to protected resources while denying access to unauthorized users. The first step in identifying a user is through a userame. The next step is to challenge the user by providing additional information such as a password or generated token value to prove that the supplied identity is authentic. Once the user has been authenticated, the next step is to see what permissions the user has. Permissions determine what the user can and cannot do. When a user requests access to a resource, the request is compared to the permissions list for that user which will determine if access will be granted or denied. This process is known as <b>access control</b>. Access controls protect resources from unauthorized access. This lab will utilize Active Directory to create several new users and groups. Folder structure will be created to align with the new groups and permissions will be assigned that will restrict user access to each folder based on group membership. Access will be verified by logging in as each user and attempting to access each folder. </p>
  
<h2>Directions</h2>
    <p>From the Windows Server taskbar, click <b>Server Manager</b> icon, to open the Server Manager application.</p>

![server manager icon](https://user-images.githubusercontent.com/107451613/177577215-136b235a-7600-40f6-a6bf-a7a5813decbc.png).

<hr>

<p>1. Select <b>Tools</b> from the Server Manager menu bar, then select <b>Active Directory Users and Computers</b>.

![ADUC](https://user-images.githubusercontent.com/107451613/177578610-469e2b16-28d0-435e-b210-ee9822ee1f04.png)

  <hr>
<p>2. In the left pane of the <b>Active Directory Users and Computers</b>console, expand the domain to show all objects in the domain. In this case, the domain is the <b>securelabsondemand.com</b> domain. 
  
![SLODD](https://user-images.githubusercontent.com/107451613/177579823-45945717-bc82-46bf-903b-000cd57bb349.png)
  
  <hr>

<p>3. Locate the <b>Users</b> container to see a list of all the existing users and groups in the domain. 
  
![ADUsers](https://user-images.githubusercontent.com/107451613/177580324-3b33cbd8-9a4a-4058-9010-5edb680f2589.png)
  
  <hr>
<p>4. Click the <b> Create a new group in the current container</b> on the Active Directory Users and Computers toolbar. This will open the New Object-Group dialog box.
  
  ![NU](https://user-images.githubusercontent.com/107451613/177581470-966a7695-01bb-40b4-9ce6-5c1cfd405b3e.png)
<hr>
<p>5. In the New Object - Group dialog box, type <b>Developers</b> in the <b>Group name:</b> box. Set the group scope to <b>Global</b> and the group type to <b>Security</b>. Once this is complete, create a new global security group named <b>Managers</b>.
  
![NewOb](https://user-images.githubusercontent.com/107451613/177581932-29f93495-29b5-47f6-bcc2-789334c93563.png)
  
  <hr>
<p>6. Now we will create a new global security group titled <b>Human Resources</b> using Powershell. 
<ul>
  <li><b>New-ADGroup</b> created a new Active Directory group. This new group is created in the Users OU by default.</li>
  <li><b>-Name</b> specified the group name.</li>
  <li><b>-GroupScope</b> determines how the group is applied to the domain. The three possible domains are: Universal, Global, or Domain Local.</li>
  <li><b>-GroupCategory</b> specifies the type of group. The two possible options for category are: Security or Distrubution(email).</li>
</ul></p>
  <hr>

<p>7. At the PowerShell prompt, type <b>New-ADGroup -Name HumanResources -GroupScope Global -GroupCategory Security</b> then press Enter to create the new group. </p>

![ADCom](https://user-images.githubusercontent.com/107451613/177585872-96c7e6d1-f59b-46bf-a295-bc404373c16c.png)

<hr>

<p>8. Restore the <b>Active Directory Users and Computer</b> window. Locate and right-click an empty area in the right pane, and click <b>Refresh</b> to verify that the new HumanResources group was added to the Users OU. </p>
![Refresh](https://user-images.githubusercontent.com/107451613/177588163-c8117525-c96d-4778-9427-030a4b8322bd.png)

<hr>

<p>9. Now we are going to add new Users to our Groups. Click <b> Create a new user in the current container</b> icon to open the New Object - User dialog box.</p>
![NewU](https://user-images.githubusercontent.com/107451613/177589984-74ac04bb-be86-4084-845d-433ae9d56b9c.png)

<hr>
<p>10. In the <b>New Object - User</b> dialog box, type the following information, then click <b>Next</b>.
<ul>
  <li>First name: <b>Sam</b></li>
  <li>Last name: <b>Carpenter</b></li>
  <li>User logon name: <b>scarpenter</b></li>
</ul></p>

![NewU](https://user-images.githubusercontent.com/107451613/177589984-74ac04bb-be86-4084-845d-433ae9d56b9c.png)

<hr>
<p>11. For the password, type the following information:
<ul>
  <li>Password: <b>P@ssw0rd!</b></li>
  <li>Confirm password:<b>P@ssw0rd!</b></li>
</ul></p>
<p>Uncheck <b>User must change password at next logon</b> checkbox, then click <b>Next</b> to continue.</p> 

![PW](https://user-images.githubusercontent.com/107451613/177596549-2cbb4b3d-b8a5-42ce-925f-9354c01888b3.png)![uncheck](https://user-images.githubusercontent.com/107451613/177597712-04e90475-09af-4b11-b913-3fbd24e6b4ef.png)

<hr>
<p>12. Click <b>Finish</b> to create the account for the new user.</p>

![NewAcc](https://user-images.githubusercontent.com/107451613/177598138-523f89d9-334c-42e5-a41c-99104d3ca1aa.png)

<hr>
<p>13. In the Users list, right-click the <b>Sam Carpenter</b> user account and select <b>Add to a group</b> </p>

![AddtoGroup](https://user-images.githubusercontent.com/107451613/177602581-49cf9afa-3dcc-435e-9f89-79b76cd9523c.png)

<hr>

<p>14. In the Select Group dialog box, type <b>Developers</b> in the <b>Enter the object name to select</b> box, then click <b>Check Names</b> to confirm that the group exists and check spelling. Click <b>OK</b> to complete the process. Click <b>OK</b> to close the success dialog box. </p>


![Dev](https://user-images.githubusercontent.com/107451613/177603444-896d0f6d-cd45-4c20-9246-684810bf2d98.png)


<p>15. Repeat these steps to create a user with the following:
  <ul>
  <li>First name: <b>Carl</b></li>
  <li>Last name: <b>Prince</b></li>
  <li>User logon name: <b>cprince</b></li>
</ul></p>
</p>
<p> Repeat steps 13 and 14 to add cprince to the <b>Developers</b> and <b>Managers</b> groups. </p>

<hr>
<p>16. Now we will create another user using PowerShell using the following command:</p>
<b>New-ADUser -Name lcasado -UserPrincipalName lcasado@securelabsondemand.com -AccountPassword (ConvertTo-SecureString -AsPlainText "P@ssw0rd!" -Force) -GivenName Laura -Surname Casado -Enabled $true </b></p>
<p>
  <ul>
  <li><b>New-ADUser</b> creates a new user account in Active Directory.</li>
  <li><b>-Name</b> specifies the name of the object in Active Directory.</li>
  <li><b>-UserPrincipalName</b> determines the logon name for the new user</li>
  <li><b>-AccountPassword</b> specifies a password for the new user account. The account password should be set once the account is created or the account will be disabled until a password is set. A password can be set using the Set-<b>ADAccountPassword</b> cmdlet in a separate step. </li>
  <li><b>-GivenName</b> sets the user's first name.</li>
  <li><b>-New-ADUser</b> sets the user's last name.</li>
  <li><b>-Enabled</b> enables the account ($true) only if a password is set.</li>
</ul></p>
<hr>
<p>17. At the PowerShell prompt, type <b>New-ADUser -Name lcasado -UserPrincipalName lcasado@securelabsondemand.com -AccountPassword (ConvertTo-SecureString -AsPlainText "P@ssw0rd!" -Force) -GivenName Laura -Surname Casado -Enabled $true</b> and press Enter to create the lcasado account.
  
  ![lcasso](https://user-images.githubusercontent.com/107451613/177608307-08e7c0b0-9222-4a14-bce3-0ca8faacb4de.png)
