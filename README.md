# File-Share-and-Permission

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

**Step 1: Creating Folders**
- Log in to DC-1 as administrator (mynetwork\jane.admin)
- Open the "C:\" drive
- Create 4 Folders as the following:
    - "write-access"
    - "read-access"
    - "no-access"
    - "accounting"
<p>  
<img src="https://github.com/AllanMontalvo/Virtualbox-Active-Directory/assets/135927674/2c6c5e6a-63a4-47e7-91db-cfbf53b65f34" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

**Step 2: Set Permission**
- Set the following Folders with these permission:
    - "write-access": Groups-"Domain Users", Permission-"Read/Write"
