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

<p>Select <b>Tools</b> from the Server Manager menu bar, then select <b>Active Directory Users and Computers</b>.

![ADUC](https://user-images.githubusercontent.com/107451613/177578610-469e2b16-28d0-435e-b210-ee9822ee1f04.png)

  <hr>
<p>In the left pane of the <b>Active Directory Users and Computers</b>console, expand the domain to show all objects in the domain. In this case, the domain is the <b>securelabsondemand.com</b> domain. 
  
![SLODD](https://user-images.githubusercontent.com/107451613/177579823-45945717-bc82-46bf-903b-000cd57bb349.png)
  
  <hr>

<p>Locate the <b>Users</b> container to see a list of all the existing users and groups in the domain. 
  
![ADUsers](https://user-images.githubusercontent.com/107451613/177580324-3b33cbd8-9a4a-4058-9010-5edb680f2589.png)
  
  <hr>
<p> Click the <b> Create a new group in the current container</b> on the Active Directory Users and Computers toolbar. This will open the New Object-Group dialog box.
  
  ![NU](https://user-images.githubusercontent.com/107451613/177581470-966a7695-01bb-40b4-9ce6-5c1cfd405b3e.png)
<hr>
<p>In the New Object - Group dialog box, type <b>Developers</b> in the <b>Group name:</b> box. Set the group scope to <b>Global</b> and the group type to <b>Security</b>. Once this is complete, create a new global security group named <b>Managers</b>.
  
![NewOb](https://user-images.githubusercontent.com/107451613/177581932-29f93495-29b5-47f6-bcc2-789334c93563.png)
  
  <hr>
Now we will create a new global security group titled <b>Human Resources</b> using Powershell. 
<ul>
  <li><b>New-ADGroup</b> created a new Active Directory group. This new group is created in the Users OU by default.</li>
  <li><b>-Name</b> specified the group name.</li>
  <li><b>-GroupScope</b> determines how the group is applied to the domain. The three possible domains are: Universal, Global, or Domain Local.</li>
  <li><b>-GroupCategory</b> specifies the type of group. The two possible options for category are: Security or Distrubution(email).</li>
</ul>
  <hr>

At the PowerShell prompt, type <b>New-ADGroup -Name HumanResources -GroupScope Global -GroupCategory Security</b> then press Enter to create the new group. 

![ADCom](https://user-images.githubusercontent.com/107451613/177585872-96c7e6d1-f59b-46bf-a295-bc404373c16c.png)

<hr>

Restore the <b>Active Directory Users and Computer</b> window. Locate and right-click an empty area in the right pane, and click <b>Refresh</b> to verify that the new HumanResources group was added to the Users OU. </p>
![Refresh](https://user-images.githubusercontent.com/107451613/177588163-c8117525-c96d-4778-9427-030a4b8322bd.png)

<hr>

Now we are going to add new Users to our Groups. Click <b> Create a new user in the current container</b> button to open the New Object - User dialog box.
![NewU](https://user-images.githubusercontent.com/107451613/177589984-74ac04bb-be86-4084-845d-433ae9d56b9c.png)

<hr>
