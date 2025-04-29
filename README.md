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
<p>Begin by creating a Windows 10 virtual machine in the Azure portal.
Assign the VM the name <b>"osticket-vm"</b>, configure it with 4 vCPUs, and set the credentials. Once created, log into the VM using Remote Desktop (RDP).</p>
  
![image](https://github.com/user-attachments/assets/4317a02c-c921-4b77-b22c-485842d91cf9)


<b>Download osTicket Installation Files</b>
<p>Once your virtual machine is ready, the next step is to prepare the necessary installation files. 
Download the <b>osTicket-Installation-Files.zip</b> from "https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6" and extract its contents to the desktop. This will make it easier to access everything during the setup.</p>
  
![image](https://github.com/user-attachments/assets/2ce1a07d-a912-4596-b359-f91f77332799)

<b>Enable IIS with CGI</b>
<p>Next, enable <b>Internet Information Services (IIS)</b> along with <b>CGI support</b>.
Go to:
<b>Control Panel</b> → <b>Programs</b> → <b>Turn Windows features on or off</b> → <b>World Wide Web Services</b> → <b>Application Development Features</b> → <b>CGI.</b></p>
  
![image](https://github.com/user-attachments/assets/66475cdd-6b19-4248-aaeb-03f39f14fb9f)

<b>Install PHP Manager for IIS</b>
<p>From the <b>osTicket-Installation-Files</b> folder, run the installer for <b>PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)</b>.</p>

![image](https://github.com/user-attachments/assets/fa696552-5728-47d5-82d0-d30a52ff547e)

<b>Install the Rewrite Module</b>
<p>Still in the same folder, install the <b>Rewrite Module</b> using the file <b>rewrite_amd64_en-US.msi</b>.</p>

![image](https://github.com/user-attachments/assets/80e80c79-9ccc-4b49-8519-d021126c214a)

<b>Set Up PHP Directory</b>
<p>Manually create a folder at <b>C:\PHP.</b>
Then unzip <b>php-7.3.8-nts-Win32-VC15-x86.zip</b> (found in the installation files) into that folder.</p>

![image](https://github.com/user-attachments/assets/df09fb65-bd78-43b9-a136-eb45a2d95f45)

<b>Install VC++ Redistributable</b>
<p>Install the <b>Visual C++ Redistributable (VC_redist.x86.exe)</b> from the installation folder.</p>

![image](https://github.com/user-attachments/assets/e9f6c2fe-711d-45b1-af6d-4e4ba0683ac1)

<b>Install MySQL</b>
<p>Now install <b>MySQL 5.5.62</b> using <b>mysql-5.5.62-win32.msi</b> from the same folder.
Use the <b>Typical Setup</b>, then:

  - Launch Configuration Wizard

  - Choose <b>Standard Configuration</b>

  - Set Username: root

  - Set Password: root</p>
  
![image](https://github.com/user-attachments/assets/54b7d818-19a4-42a0-a336-f4f825e699d4)

<b>Register PHP with IIS</b>
<p>Open IIS as Administrator.
In the PHP Manager, register PHP by pointing it to: <b>C:\PHP\php-cgi.exe</b></p>
  
![image](https://github.com/user-attachments/assets/fd90c2cd-b41a-4c52-a2fd-938d814aa8e1)

<b>Install osTicket</b>
<p>From the installation folder, unzip <b>osTicket-v1.15.8.zip</b>. Copy the <b>upload</b> folder into <b>C:\inetpub\wwwroot</b> and rename it to <b>osTicket</b>.</p>
  
![image](https://github.com/user-attachments/assets/0ff3dde2-28c1-421a-a92a-9982d3f5552c)

<b>Reload IIS</b>
<p>Return to IIS and stop/start the server again to apply changes.</p>

![image](https://github.com/user-attachments/assets/dacdec1b-0ba2-4750-bac2-95e1d805ea05)

<b>Browse to osTicket in IIS</b>
<p>In IIS Manager:

  - Go to <b>Sites</b> > <b>Default Web Site</b> > <b>osTicket</b>

  - On the right panel, click <b>*“Browse :80”</b> to launch osTicket in your browser.</p>

![image](https://github.com/user-attachments/assets/30b73bdb-0f00-4f6e-b61a-1a0049d219d0)

<b>Configure PHP Extensions</b>
<p>Before proceeding, a few PHP extensions must be enabled. In your PHP configuration, ensure that <b>php_imap.dll</b>, <b>php_intl.dll</b>, and <b>php_opcache.dll</b> are activated.</p>
  
![image](https://github.com/user-attachments/assets/679d45a3-dba7-4140-9c78-7eff90532f50)

<b>Configure osTicket Configuration File and Set Permissions</b>
<p>Now that osTicket is accessible in the browser, it’s time to configure its main settings file.

First, navigate to:
<b>C:\inetpub\wwwroot\osTicket\include</b>.
Locate the file named <b>ost-sampleconfig.php</b>, then rename it to <b>ost-config.php</b>.

Next, you’ll need to adjust the file permissions to allow the installer to write to it.
Right-click on <b>ost-config.php</b>, select <b>Properties → Security → Advanced</b>, then:

  1. Disable inheritance

  2. Remove all existing permission entries

  3. Add a new permission for <b>“Everyone” and grant Full Control</b></p>
  
![image](https://github.com/user-attachments/assets/88b83894-197c-49d3-a37e-0e9d157429cc)

<b>Setup Database Using HeidiSQL</b>
<p>From the osTicket files folder, install <b>HeidiSQL</b>.
Open it, and:

  - Create a new session using <b>root/root</b>

  - Connect to the session

  - Create a new database called <b>osTicket</b></p>
  
![image](https://github.com/user-attachments/assets/1309989c-5c04-4dce-8940-d1cb536742a9)

<b>Complete osTicket Setup in Browser</b>
<p>Now that the file and database configurations are in place, return to your browser where the osTicket installer is open.

Start by filling in the basic helpdesk information:

  - Helpdesk Name 

  - Default Email Address — this will be used to receive customer support requests

Scroll down to the Database Settings section and enter the following:

  - MySQL Database: osTicket

  - MySQL Username: root

  - MySQL Password: root

Once everything is filled out, click <b>“Install Now!”</b> to complete the installation.

If all configurations are correct, osTicket will install successfully and redirect you to the admin login screen.</p>
     
![image](https://github.com/user-attachments/assets/9beb26c2-aa4d-412b-9cce-f5bbbfe545cc)
