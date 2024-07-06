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

![image](https://github.com/ahmadspain/osticket-prereqs/assets/158358030/f37cd686-2ffb-4e52-bece-7a6bdb82cde5)

Installing IIS and PHP Manager:
- Install IIS with CGI and Common HTTP Features
- Download and install PHP Manager for IIS
- Download and install the Rewrite Module.

<br />

![image](https://github.com/ahmadspain/osticket-prereqs/assets/158358030/f434b612-5d4b-4a25-879e-fd2f0b64f9b3)

Set up PHP:
- Create directory C:\PHP.
- Download PHP 7.3.8 and extract the contents to C:\PHP.
- Install VC_redist.x86 (C++ Redistributable).

Configure IIS:
- Open IIS as Admin.
- Register PHP.
- Reload IIS.
<br />

![image](https://github.com/ahmadspain/osticket-prereqs/assets/158358030/d5cd42ff-550f-47c4-868c-dc81fc70aa15)

Install MySQL:
- Download and install MySQL with Standard Configuration and set password to "Password1".
- Open IIS as Admin.
- Register PHP.

<br />

![image](https://github.com/ahmadspain/osticket-prereqs/assets/158358030/1f3da7f6-7a24-4963-b0c6-5a234119784d)

Install osTicket:
- Download osTicket.
- Extract "upload" folder to c:\inetpub\wwwroot and rename it to "osTicket".
- Reload IIS.

Configure PHP Extensions:
- Open PHP Manager in IIS.
- Enable php_imap.dll, php_intl.dll, and php_opcache.dll.
- Refresh the osTicket site in your browser.

Setup osTicket:
- Rename ost-config.php from ost-sampleconfig.php and configure permissions.
- Complete osTicket setup in the browser with Helpdesk name and Default email.

Configure MySQL Database:
- Install HeidiSQL.
- Create a new session with root/Password1.
- Connect and create a database named "osTicket".

Finish osTicket Setup:
- Continue osTicket setup in the browser with MySQL Database, Username (root), Password (Password1), and click "Install Now!"
<br />

![image](https://github.com/ahmadspain/osticket-prereqs/assets/158358030/f891dcb1-33b4-42dd-ab6e-4a7a222b0837)

<p>
osTicket is successfully installed and running!
</p>
<br />
