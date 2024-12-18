<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket -Prerequisites, Installation, Configuration, Admin and Helpdesk panel view, Ticket Lifecycle</h1>

![image](https://github.com/user-attachments/assets/73f0b1ff-311a-4399-b226-fd03c30107b2)

What is being done?<br />

-Setup a Virtual Machine in Azure<br />
-install the osTicket requirements<br />
-install osTicket<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 pro x64</b> (22H2)

<h2>List of Prerequisites</h2>

- HeidiSQL_12.3.0.6589
- mysql-5.5.62-win32
- osTicket-v1.15.8
- PHPManagerForIIS_V1.5.0
- rewrite_amd64_en-US
- VC_redist.x86

<h2>Steps</h2>

![image](https://github.com/user-attachments/assets/7de54449-3e28-4c3f-a4f7-a2377dd8cb20)

Create an Azure Virtual Machine Windows 10, 4 vCPUs
- Name: osticket-vm
- Username: labuser
- Password: osTicketPassword1!
<br />

Log into the VM with Remote Desktop Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop.


![image](https://github.com/user-attachments/assets/accbf9d4-d764-4f05-8ffb-1dc490738812)


Next, we will enable IIS(Internet Information Services) to make our VM a webserver with CGI, Dependency that osTicket needs from Control panel by turning windows features on 

![image](https://github.com/user-attachments/assets/286a31d1-118d-4814-88a6-9cf4f0a0d425)


From the “osTicket-Installation-Files” folder, install PHP Manager for IIS
(PHPManagerForIIS_V1.5.0.msi) and install the Rewrite Module (rewrite_amd64_en-US.msi) and Create the directory C:\PHP
![image](https://github.com/user-attachments/assets/e7012065-e7c5-48b2-a37e-a4bbdfd8ac45)

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8(php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
![image](https://github.com/user-attachments/assets/3ecdc732-fddc-4610-ac23-53495f3151a4)

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe, install MySQL(DB) 5.5.62
(mysql-5.5.62-win32.msi)
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Username: root
- Password: root
- 
![image](https://github.com/user-attachments/assets/9ef8f157-db45-4642-8426-20273bfaab52)

Next, Open IIS as an Admin, double click php manager , Register new PHP Version, browse to c:\PHP\php-cgi.exe

![image](https://github.com/user-attachments/assets/dde81fa1-1a9e-4cf0-923d-f5b69d359da2)
![image](https://github.com/user-attachments/assets/e6b50a86-3383-4281-858a-71ff0cea05fe)

Reload IIS (Open IIS, Stop and Start the server)
![image](https://github.com/user-attachments/assets/ef72f4e5-78fb-4d3c-9a0f-aebbffd691da)

<h2>osTicket Installation</h2>

Next,Install osTicket v1.15.8. From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”. Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

![image](https://github.com/user-attachments/assets/de4f9661-2f28-414b-a631-96723e77a829)

Reload IIS (Open IIS, Stop and Start the server). Go to sites -> Default -> osTicket, On the right, click “Browse *:80”


![image](https://github.com/user-attachments/assets/f48c5448-e242-4f44-9c3d-cfaaab37d412)

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
![image](https://github.com/user-attachments/assets/a5eba3de-22e9-4be6-a5cb-d75905fc1188)

![image](https://github.com/user-attachments/assets/f4d43852-9986-411a-a5d0-1178f0b9f1d1)


Rename: ost-config.php. From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php. Disable inheritance -> Remove All. New Permissions -> Everyone -> All

![image](https://github.com/user-attachments/assets/e36b5722-eef2-415a-96c5-d7eea3106679)

![image](https://github.com/user-attachments/assets/16868324-957c-4cf6-b43f-fb5e91edc5c1)

![image](https://github.com/user-attachments/assets/fb5e9769-f08e-4749-873e-4b81bf9d91b9)

![image](https://github.com/user-attachments/assets/9a05680e-5a4b-4633-8960-24906ed9c710)

From the “osTicket-Installation-Files” folder, install HeidiSQL. Open Heidi SQL. Create a new session, root/root and Connect to the session, Create a database called “osTicket”

![image](https://github.com/user-attachments/assets/33c05c36-9a36-4473-aef5-28840a94500c)

![image](https://github.com/user-attachments/assets/2109d7e9-1db8-4fa3-b915-a45b1d0a44f8)

![image](https://github.com/user-attachments/assets/22ce51dd-200b-4f20-9bb0-8d41e7e2da7c)

![image](https://github.com/user-attachments/assets/87ccad93-f0fc-4f0d-8995-8c50fc8671dd)

Continue Setting up osTicket in the browser. MySQL Database: osTicket. MySQL Username: root. MySQL Password: root. Click “Install Now!”

![image](https://github.com/user-attachments/assets/f55bf3bf-b9c5-48a0-89d2-422faaa818de)













