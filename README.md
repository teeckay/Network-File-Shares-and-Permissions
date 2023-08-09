# Network-File-Shares-and-Permissions

<p align="center">
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/6c0c536e-ae4c-42a2-b106-c60b491e8f03)


</p>

<h1>Network File Sharing And Permissions On Active Directory Deployed in the Microsoft Azure Cloud </h1>
This tutorial outlines the implementation of Permissions and File Sharing on Active Directory<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
  
<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create some sample file shares with various permissions.
- Step 2: Attempt to access file shares as a normal user.
- Step 3: Create an “ACCOUNTANTS” Security Group, assign permissions, an test access. 

<p>
<h2>Deployment and Configuration Steps</h2>

<p>
  
To illustrate File Sharing and Permissions on a Network for this lab, I will log into a Domain Controller ( Active Directory)  installed in a virtual machine named DC-1. I will also log in with a user, Deon Cool, in the domain from a separate client virtual machine called Client-1.

</p>

<h2> Step 1: Create some sample file shares with various permissions.</h2>

</p>

<p>
  
I will then create the following folders on the Domain Controller’s C: drive for the purpose of this exercise : read-access, write-access, no-access and accounting folders, respectively, to show how permissions work on a network. 
</p>
<br />

<p>
I begin by first giving read permission level to domain users to the read-access folder.
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/4acb6dbe-84c2-4650-a9ad-4d3e66e9bd66)

</p>

<p>
  
Next, I give Write ( Read/Write) permission level to Domain Users to the write-access folder.

</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/323ad1ec-4f0b-41a4-a2cc-9d12e707f601)

</p>

<p>
  
Next, I give Read/Write permission level to Domain Admins to the no-access folder. This denies access to Domain Users and allows access to Domain Admins to this folder. 
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/16cfa5ee-be0f-4c0f-9d50-153eb06fe95e)

</p>

<p>
  
Next, I use Deon Cool’s ( A Domain User ) login to the client-1 virtual machine connected to the domain controller to browse to the created folders: read-access, write-access and no access. As expected, there is a restriction while trying to open the no-access folder. The read-access folder allows this user to open the folder and view its contents but not create any files or folders. And the write-access folder does allow viewing and creating documents as seen below. Access to the no-access folder is restricted to a normal user ( a Domain User ).
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/2eeb39dd-283c-4fbc-a5e1-0ca122bdaa5d)

</p>

<p>
  
Access to view the read-access folder contents is granted, but making a new folder or document within the folder is denied. To further illustrate this point, I will save a document in this folder on the domain controller to show that this user can only view and open the document but not make or write any documents or folders.
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/9df5e10c-b055-4613-a949-44db4fb77d6e)

![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/683e98d3-ee60-48b4-93c0-59784c167697)


</p>

<p>
  
This user can view the contents of the folder and open the text document to view it.
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/4338aff2-6c09-4307-9299-5cf92b0c4179)

</p>

<p>
  
Access is granted to the write-access folder and also writing and saving a new text document.
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/ae1cf86d-723b-400d-966e-dd84baba0260)

</p>

<p>
  
Next, I add an accountants security group on the Domain Controller to Illustrate file sharing on the Accountants folder
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/2115bdea-784f-4285-b60a-c057a6c2d253)

</p>

<p>
  
Next, I give the accountants security group Read/Write access to the accounting folder.

</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/f55f0887-89c6-4f51-917c-466fcbd50e00)

</p>

<p>
  
Next, I go to the client computer and look at the network share folders to the domain controller. The accounting folder can be seen but cannot be accessed; this is because Deon Cool is logged in as a Domain User and is not a member of the accounting group. 
</p>
<br />

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/c05cc0ae-4b57-4a3e-a471-d90d5fdeb8ae)

</p>

<p>
  
To fix this issue, I go to the Domain Controller Active Directory and add Deon Cool to the Accountants security group as seen below.
</p>
<br />

<p>

<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/1cf83b82-af23-4b7a-b9a8-87a9837d39b8)

</p>
<br />

<p>
<p>
  
For the new permissions to access the accounting folder to take effect for Deon Cool, I log him out of the domain then back in. And he can now access the accounting folder.
</p>
<br />

<p>
<p>
  
![image](https://github.com/teeckay/Network-File-Shares-and-Permissions/assets/64244011/a22dec67-1110-4e4c-a7ec-640d9a0133d4)

</p>
<br />

