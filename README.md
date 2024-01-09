<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Network File Sharing and Permissions</h1>
This tutorial details how to grant specific file permissions to users.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Creating Network Folders and Setting Permissions
- Adding Groups within organizational units
- Confirming group permissions


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/DC-1%20Static%20Address.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


</p>
<p>
Create a group resource and virtual machines within Microsoft Azure. Reference https://github.com/chrisrraP/configure-ad on how to create virtual machines. Log into server (DC-1) and create 3 folders titled after their permission settings (read-access, write-access, and no access). Create a fourth folder called "accountants".
<br />

<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/DC-1%20Firewall%20Setup.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/DC-1%20Add%20Forest.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/DC-1%20Add%20User%20Role.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
I log into the domain server and enable ICMPv4 TCP Protocols on Windows Firewall. Once connectivity is established between both machines, I install Active Directory and add a domain. The machine restarts by default and I log back in with the new domain I created and the pre-existing username. I create Organizational Units (OU) and a couple of users. I give one of the users administrator properties by adding them to "Domain Admins" group. 
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/Change%20Client%20one%20DNS%20Server.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/Confirm%20Client%20Server%20Changed.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I use the Microsoft Azure portal to change the DNS settings of the client machine to the server's private IP address. I ensure connectivity and then log back into the server to verify that my "client" computer is listed in the "computers" container of the Active Directory domain root.
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/Allow%20users%20server%20access.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/Generate%20Random%20Users.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Logged back into the client machine with the admin user login and allowed domain users access to remote desktop via system properties. I then log out and log into the domain as the admin user. Using powershell as an administrator allows me to run a script that generates random users to the OU within Active Directory.
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/configure-ad/blob/main/Login%20as%20new%20user%20to%20server.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly, I pick a random user from the OU and log into the client machine. 
</p>
<br />
