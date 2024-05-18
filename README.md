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
- Set the following Folders with these permissions:
    - "write-access" - Groups: "Domain Users", Permission: "Read/Write"
 
<p>
     <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/ad5e6efa-9d7f-4485-af80-b4e6b175bf92" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
   
    - "read-access" - Groups: "Domain Users", Permission: "Read"
<p>
     <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/734b894b-ead4-45a5-89bc-412df4acca84" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>

    - "no-access" - Groups: "Domain Admin", Permission: "Read/Write"
    - "accounting" - Groups: "Accountants", Permission: "Read/Write"
 

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




