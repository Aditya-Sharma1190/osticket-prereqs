<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket -Installation, Configuration, Admin and Helpdesk panel view, Ticket Lifecycle</h1>

![image](https://github.com/user-attachments/assets/73f0b1ff-311a-4399-b226-fd03c30107b2)

What is being done?<br />

-Setup a Virtual Machine in Azure<br />
-install the osTicket requirements<br />
-install osTicket<br />
-Configuration<br />
-Explore osTicket from a Help Desk Perspective<br />
-create, interact, close tickets<br />


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

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe, install MySQL 5.5.62
(mysql-5.5.62-win32.msi)
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Username: root
- Password: root



