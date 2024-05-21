<h1>File Share and Permission</h1>
This tutorial outlines the implementation of file share and set permissions in a shared network.<br />

<h2>Prerequisite</h2>
In this project, you should have created a server and a client connected within the same network. If you have not done so, please use this link to take you to <a href="https://github.com/AllanMontalvo/Virtualbox-Active-Directory">Configuring On-premises Active Directory</a> to create your small network and begin this project.

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
    <p>
        <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/c4cbc474-71fb-48b0-a648-33c3cd4e8d2b" height="60%" width="60%" alt="Disk Sanitization Steps"/>
    </p>
    
    - "read-access" - Groups: "Domain Users", Permission: "Read"
    <p>
      <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/20b2eb28-dd84-4d73-91c1-884de8c682d9" height="60%" width="60%" alt="Disk Sanitization Steps"/>
    </p>
    
    - "no-access" - Groups: "Domain Admin", Permission: "Read/Write"
    <p>
      <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/93f84d7c-6ef7-41b6-9c3c-8ae6926d02dc" height="60%" width="60%" alt="Disk Sanitization Steps"/>
    </p>
  

 

<h3>User Test</h3>

**Step 4: Open Folder Location**
- Log in to Client-1 as a normal user (mydomain\someone).
- Open "run" and type "\\dc-1".
- You should see the 3 folders we created.
<p>
      <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/780fdb22-237b-4aca-ab66-c8d5a15455e1" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 5: Access the folders**
- Have the normal user try to open each folder.
    - "write-access" - able to edit/create documents in the folder and read documents.
    <p>
      <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/7f563dda-19f8-4fa7-a32a-ef9cfc9674c2" height="60%" width="60%" alt="Disk Sanitization Steps"/>
    </p>
  
    - "read-access" - able to read documents but cannot edit/create documents in the folder.
    <p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/66d433d7-4dbf-4665-99d3-6a10fd9c220f" height="60%" width="60%" alt="Disk Sanitization Steps"/>
    </p>

    - "no-access" - unable to access the folder.
     <p>
     <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/f576e7ee-e62b-4a2b-8fc6-f90b11e7167f" height="60%" width="60%" alt="Disk Sanitization Steps"/>
     </p>
 
 
<h3>Add User into Account Group</h3>

**Step 6: Create Accountant Group**
- Log in to DC-1 as administrator (mynetwork\jane.admin).
- Open Active Directory.
- Right-click mydomain.net and create a new Organization Group called "_SECURITY_GROUP" under mydomain.net.
- Within "_SECURITY_GROUP", right-click and create a new group called "Accountants".
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/5d58bc42-2e91-410f-a35e-3381086e78e5" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 7: Set Permission for Accounting Folder**
- Open the \\C: drive
- Right-click on the “accounting” folder and select “Properties”
- Under “Sharing” tab, select share.
- Type the group name for the folder and then select “Add” to the group.
- Set the following Folders with these permissions:
    - "accounting" - Groups: "Accountants", Permission: "Read/Write"
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/6dc7e09a-1d89-4053-82a7-672a39675a3f" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 8: Accounting Folder Test**
- Back on file explore refresh and you will see “accounting” folder.
- Have user <someone> try to open "accounting" folder.
    - "accounting" - unable to access the folder because the user is not part of the "Accountant" Group.
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/853f03ad-a56f-4072-84ff-7cb0efb2c3d0" height=60%" width="60%" alt="Disk Sanitization Steps"/> 

</p>


**Step 9: Add User to Accountant Group**
- Double-click “ACCOUNTANTS” and under “Members” tab, select “Add”.
- Type username <someone> and select “Check Names” to verify username exits then select “OK”.
- Select “Apply” then select “OK”
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/1afd8cc7-1d01-4254-9e17-41d5ddb9c15a" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 10: Verify Access**
- Log off and log back into Client-1 as the user (mydomain\someone).
- Open "run" and type "\\dc-1".
- Try to access "accounting" folder.
    - "accounting" - able to edit/create documents in the folder and read documents.
<p>
    <img src="https://github.com/AllanMontalvo/File-Share-and-Permission/assets/135927674/77e0c7ea-3aca-441a-8055-b497c8a1c570" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
 
<h2>Final Notes</h2>
In conclusion, this project demonstrates creating shared folders and setting appropriate permissions. Working on this file-sharing project has deepened my understanding of its application in an enterprise setting. I learned how to manage access across multiple departments, ensuring users can securely access their folders. This approach is also useful for special projects requiring specific permissions for selected users. The skills and insights gained from this experience are valuable for both professional and personal file management.




