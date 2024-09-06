<h1>Configuring Active Directory(IN PROGRESS)</h1>

<br />
<h2>Description</h2>
Text

<h2>Utilities Used</h2>

- <b>Sever Manager</b>
- <b>Active Directory Users and Computers (AD UC)</b>
- <b>Group Policy Management Editor</b>

<h2>Environments Used </h2>

- </b>Windows Sever 2022 through Oracle Virtual Box</b>
- </b>Windows 10 Pro</b>

<h2>Lab Overview:</h2>

<p align="center">
I first began experimenting with Organizational Units (OUs). In AD UC I created an OU called HR for Human Resources and under the Users Directory, I clicked and moved john smith into the new HR OU.<br/>
<img src="https://github.com/user-attachments/assets/be7b79c3-1e55-47ea-92e5-f89b83434490" alt="Configuring AD"/>
<br />
<br />
With the newly created OU, I could now experiment with Group Policy Management, a critical part of Active Directory domain/user management. I decided to change a very important setting, Account lockout threshold which I found under Computer Configuration meaning no matter the user that logged on, that policy is on the computer that connected with the Domain Controller. It was in security settings, and i changed to be after five incorrect password login attempts it would lock the account for five minutes. While this might not be security best pratices, this was just me experimenting in a lab environment.<br/>
<img src="https://github.com/user-attachments/assets/3cc65960-0624-4550-9c53-c2ba1ede972b" alt="Configuring AD"/>
<img src="https://github.com/user-attachments/assets/8578e4d0-77a6-417d-879f-1b779bdbb25a" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />
Text<br/>
<img src="" alt="Configuring Directory"/>
<br />
<br />




<h2>Thoughts</h2>
text
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
