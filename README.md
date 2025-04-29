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

- Azure Virtual Machine
- osTicket Installation files 
- Heidi SQL


<h2>Installation</h2>

<b>Create an Azure Virtual Machine</b>
<p>To start, you'll need to create a new virtual machine (VM) in Microsoft Azure. Log into the Azure portal and navigate to the "Virtual Machines" section. Click on "Create" and choose "Azure Virtual Machine." Configure the basic settings by selecting Windows 10 as the operating system. Name the VM "osticket-vm" to keep it easily identifiable. When choosing the size of the VM, make sure to select a configuration that provides 4 vCPUs to ensure it has enough processing power for future tasks. Complete the remaining setup steps (such as networking and storage) with default or recommended options, then deploy the VM.
  
![image](https://github.com/user-attachments/assets/4317a02c-c921-4b77-b22c-485842d91cf9)


<b>Download and Prepare osTicket Installation Files</b>
<p>Once your virtual machine is ready, the next step is to prepare the necessary installation files. 
Download the osTicket-Installation-Files.zip from the provided source and extract its contents to the desktop. This will make it easier to access everything during the setup. https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6</p>
  
![image](https://github.com/user-attachments/assets/2ce1a07d-a912-4596-b359-f91f77332799)

<b>Install and Enable IIS</b>
<p>Next, you'll need to install Internet Information Services (IIS) to host your web application. Open the Control Panel, navigate to Programs, and click on Turn Windows features on or off. From there, expand World Wide Web Services, go to Application Development Features, and enable CGI.</p>
  
![image](https://github.com/user-attachments/assets/8f7bf924-b03c-405a-a069-d40a3a5f1e4d)

<b>Install PHP and Rewrite Module</b>
<p>With IIS enabled, it’s time to add support for PHP. Install the PHP Manager for IIS and the URL Rewrite Module, both of which are included in the osTicket installation files you downloaded earlier.</p>

![image](https://github.com/user-attachments/assets/fa696552-5728-47d5-82d0-d30a52ff547e) ![image](https://github.com/user-attachments/assets/80e80c79-9ccc-4b49-8519-d021126c214a)


<b>Set Up PHP</b>
<p>After installing the necessary tools, set up PHP manually. Start by creating a new directory at C:\PHP. Then, extract the contents of PHP 7.3.8 into the C:\PHP folder.</p>

![image](https://github.com/user-attachments/assets/df09fb65-bd78-43b9-a136-eb45a2d95f45)

<b>Install MySQL</b>
<p>Now, you'll need a database system. Install MySQL 5.5.62 from the files. Set the username to "root" with a password of "root". This straightforward setup will make it easier to connect osTicket to the database later.</p>
  
![image](https://github.com/user-attachments/assets/54b7d818-19a4-42a0-a336-f4f825e699d4)

<b>Register PHP with IIS</b>
<p>Once PHP is set up, you must link it to IIS. Open the PHP Manager in IIS, and use it to register PHP with the server. This step ensures that the web server can correctly process PHP files for osTicket.</p>
  
![image](https://github.com/user-attachments/assets/fd90c2cd-b41a-4c52-a2fd-938d814aa8e1)

<b>Install osTicket</b>
<p>Now you’re ready to install osTicket itself. Begin by unzipping osTicket-v1.15.8.zip. Locate the "upload" folder inside, and copy it to C:\inetpub\wwwroot. Once copied, rename the folder to "osTicket".</p>
  
![image](https://github.com/user-attachments/assets/0ff3dde2-28c1-421a-a92a-9982d3f5552c)

<b>Configure PHP Extensions</b>
<p>Before proceeding, a few PHP extensions must be enabled. In your PHP configuration, ensure that php_imap.dll, php_intl.dll, and php_opcache.dll are activated.</p>
  
![image](https://github.com/user-attachments/assets/679d45a3-dba7-4140-9c78-7eff90532f50)

<b>Set Permissions for ost-config.php</b>
<p>With the files in place, modify the configuration file. First, rename ost-sampleconfig.php to ost-config.php. Then, right-click the file, go to Properties, and adjust its security settings.
Remove inheritance and grant "Everyone" full control to prevent permission issues during the installation.</p>
  
![image](https://github.com/user-attachments/assets/88b83894-197c-49d3-a37e-0e9d157429cc)

<b>Setup Database Using HeidiSQL</b>
<p>Before creating the osTicket database, you’ll first need to install HeidiSQL.
Once installed, open HeidiSQL and create a new session using the credentials username: root and password: root.
After connecting to the session, create a new database and name it "osTicket".
This database will store all the ticketing system’s data.</p>
  
![image](https://github.com/user-attachments/assets/1309989c-5c04-4dce-8940-d1cb536742a9)

<b>Complete osTicket Setup in Browser</b>
<p>After preparing the database, it's time to complete the web-based installation. Open a browser and navigate to http://localhost/osTicket. Follow the on-screen prompts and configure the database settings with:

    MySQL Database: osTicket

    MySQL Username: root

    MySQL Password: root

After entering the details, finish the setup to launch osTicket.</p>
     
![image](https://github.com/user-attachments/assets/9f91903a-b30e-4ebc-895f-3fe2ef2d7b31)

<b>osTicket is Successfully Installed and Running</b>
<p>Congratulations! If you followed all the steps carefully, osTicket should now be fully installed and running on your Azure virtual machine. You can start configuring your help desk system as needed.</p>

![image](https://github.com/user-attachments/assets/9beb26c2-aa4d-412b-9cce-f5bbbfe545cc)
