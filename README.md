<h1>File Share and Permission</h1>
This tutorial outlines the implementation of file share and set permissions.<br />

<h2>Environments and Technologies Used</h2>

**Technologies and Servies**
- Oracle VM VirtualBox
- Active Directory Domain Services

**Environment/Operating System**
- Windows Server 2022
- Windows 10

<h2>High-Level Deployment and Configuration Steps</h2>

<h3>Setup Permission</h3>

**Step 1: Creating Folders**
- Log in to DC-1 as administrator (mynetwork\jane.admin).
- Open the "C:\" drive.
- Create 4 Folders as the following:
    - "write-access"
    - "read-access"
    - "no-access"
    - "accounting"

 <p>  
<img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/01bd7c50-0526-42d8-a707-789465890512" height="60%" width="60%" alt="Disk Sanitization Steps"/>
 </p>

**Step 2: Create Documents**
- Create a text file for each folder.

<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/a885d916-e5c8-44c4-870e-ad2402524acb" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 3: Set Permission**
- Right-click on the folder and select “Properties”
- Under “Sharing” tab, select Share.
- Type the group name for the folder and then select “Add” to the group.
- Set the following Folders with these permissions:
    - "write-access" - Groups: "Domain Users", Permission: "Read/Write"
    - "read-access" - Groups: "Domain Users", Permission: "Read"
    - "no-access" - Groups: "Domain Admin", Permission: "Read/Write"
 
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/4df16bf0-dcbb-425c-8d86-48d890131ac5" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
  
 
  <p>
      <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/20b2eb28-dd84-4d73-91c1-884de8c682d9" height="60%" width="60%" alt="Disk Sanitization Steps"/>
  </p>
  

 

<h3>User Test</h3>

**Step 4: Open Folder Location**
- Log in to Client-1 as a normal user (mynetwork\someone).
- Open "run" and type "\\dc-1".
- You should see the 4 folders we created.

**Step 5: Access the folders**
- Have the normal user try to open each folder.
    - "write-access" - able to edit/create documents in the folder and read documents.
    - "read-access" - able to read documents but cannot edit/create documents in the folder.
    - "no-access" - unable to access the folder.
    - "accounting" - unable to access the folder because the user is not part of the "Accountant" Group.
 
<h3>Add User into Account Group</h3>

**Step 6: Create Accountant Group**
- Log in to DC-1 as administrator (mynetwork\jane.admin).
- Open Active Directory.
- Create a new Organization Group called "Security Group".
- Within the group create a new group called "Accountants.

**Step 7: Add User to Accountant Group**
- add the user(someone) as a member of "Accountants"

**Step 8: Verify Access**
- Log in to Client-1 as a user(someone).
- Open "run" and type "\\dc-1".
- Try to access "accounting" folder.
    - "accounting" - able to edit/create documents in the folder and read documents.
 
<h2>Final Notes</h2>




