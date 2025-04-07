<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Enable IIS (Internet Information Services)
- Install Web Platform installer 
- Install mySQL; set up the username and password
- Configure permissions and install osTicket


<h2>Installation</h2>

<b>1. Create Azure Virtual Machine</b>
- Create a Windows 10 VM named "osticket-vm" with 4 vCPUs.
  
![image](https://github.com/user-attachments/assets/4317a02c-c921-4b77-b22c-485842d91cf9)


<b>2. Download and Prepare osTicket Installation Files</b>
- Download <b>osTicket-Installation-Files.zip</b> and unzip it to the desktop.
  
![image](https://github.com/user-attachments/assets/2ce1a07d-a912-4596-b359-f91f77332799)

<b>3. Install and Enable IIS</b>
- Enable IIS with CGI: Go to Control Panel > Programs > Turn Windows features on or off > World Wide Web Services > Application Development Features > CGI.
  
![image](https://github.com/user-attachments/assets/8f7bf924-b03c-405a-a069-d40a3a5f1e4d)

<b>4. Install PHP and Rewrite Module</b>
- Install PHP Manager for IIS and Rewrite Module from the osTicket files.

![image](https://github.com/user-attachments/assets/fa696552-5728-47d5-82d0-d30a52ff547e) ![image](https://github.com/user-attachments/assets/80e80c79-9ccc-4b49-8519-d021126c214a)


<b>5. Set Up PHP</b>
- Create a directory C:\PHP.
- Unzip PHP 7.3.8 into C:\PHP.

![image](https://github.com/user-attachments/assets/df09fb65-bd78-43b9-a136-eb45a2d95f45)

<b>6. Install MySQL</b>
- Install MySQL 5.5.62 with the username "root" and password "root".
  
![image](https://github.com/user-attachments/assets/54b7d818-19a4-42a0-a336-f4f825e699d4)

<b>7. Register PHP with IIS</b>
- Register PHP using PHP Manager in IIS.
  
![image](https://github.com/user-attachments/assets/fd90c2cd-b41a-4c52-a2fd-938d814aa8e1)

<b>8. Install osTicket</b>
- Unzip osTicket-v1.15.8.zip and copy the "upload" folder to C:\inetpub\wwwroot and rename it to "osTicket".
  
![image](https://github.com/user-attachments/assets/0ff3dde2-28c1-421a-a92a-9982d3f5552c)

<b>9. Configure PHP Extensions</b>
- Enable required PHP extensions: php_imap.dll, php_intl.dll, php_opcache.dll.
  
![image](https://github.com/user-attachments/assets/679d45a3-dba7-4140-9c78-7eff90532f50)

<b>10. Set Permissions for ost-config.php</b>
- Rename ost-sampleconfig.php to ost-config.php and set permissions to remove inheritance and allow "Everyone" full control.
  
![image](https://github.com/user-attachments/assets/88b83894-197c-49d3-a37e-0e9d157429cc)

<b>11. Setup Database (HeidiSQL)</b>
- Open Heidi SQL
- Create a new session, root/root
- Connect to the session
- Create a database called “osTicket”
  
![image](https://github.com/user-attachments/assets/1309989c-5c04-4dce-8940-d1cb536742a9)

<b>12. Complete osTicket Setup in Browser</b>
- Access the installation via "http://localhost/osTicket" and follow prompts to configure database settings:
   - MySQL Database: osTicket
   - MySQL Username: root
   - MySQL Password: root
     
![image](https://github.com/user-attachments/assets/9f91903a-b30e-4ebc-895f-3fe2ef2d7b31)

<b>13. osTicket is successfully installed and running.</b>

![image](https://github.com/user-attachments/assets/9beb26c2-aa4d-412b-9cce-f5bbbfe545cc)
