<h1>Configuring and Troubleshooting Active Directory(IN PROGRESS)</h1>

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
One of the most common problems with an account is that a user forgets their passwords and gets locked out of there account. I simulated this by inputting the wrong password when logging into john smith. On the helpdesk account or the domain controller itself, I could open AD UC, find john smith in the HR OU, double click on this account name and a window with many tabs opens. I first went to Account, and unlocked his account, and when right clicking his name there is a window that says reset password. This pop-up appeared to also allow me to unlock his account but also me to reset his password. In this case, I created a temporary password, and checked the box that requires the user, john smith, to change the password when logging in for security and aduiting reason because proper security principles state that only one user should know the password to an account. This is seen in action when john logs back in, the temporary password is already populated and he just needs to change his password now.<br/>
<img src="https://github.com/user-attachments/assets/3ec7feab-34b3-4e25-bd08-ffaee8e96122" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/884e8ca9-db28-4bc5-8928-de13e6849a6f" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/ed899abf-1a31-4fc9-b06c-e5babae66a76" alt="Configuring Directory"/>
<br />
<br />
In another troubleshooting scenario, when the user attempts to log into, they are presented with the message, "The user's account has expired." This would prevent them from logging in and likely result in them contecting helpdesk/IT support. To remedy this issue, I would once again use AD UC, and if I did not know where the user was located, I could right click on the domain, use the search feature, change filter to Entire Directory, and then input the user's name. Double clicking on the user and going to Account, at the bottom, you can change the account expiration to a future date or check the box that sets the account to never expire.<br/>
<img src="https://github.com/user-attachments/assets/c8f5f302-3863-4745-b05a-81610aa48732" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/e5456fdf-c93f-4235-9047-6c26ff011892" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/e8111255-7e74-451a-9804-ded4c68cce1d" alt="Configuring Directory"/>
<br />
<br />
Next, the issue and troubleshooting method is a bit more complex, maybe there is an easier way to go about it. A user is attempting to login, and is met with the message, "The seucity database on the server does not have a computer account for this workstation trust realtionship." Maybe an admin accidently deleted the computer from the computer group in AD UC. To solve this, I log in a local user, in case the administrator by using ".\" to force the local authentication. I moved the computer off the domain into a workgroup and then back to the ADLab.local domain, restarted the computer and the computer re-joined the domain and can be seen in the Computers tab in AD UC.  <br/>
<img src="https://github.com/user-attachments/assets/e7890f71-cf0e-4431-862b-deb755fed507" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/6e2abe5e-2cab-447e-8b07-7d22131d38c4" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/940be1bc-7ff3-429f-b43d-61ecf7e8e6df" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/af876dcc-363b-422a-ae1b-8cc86934d547" alt="Configuring Directory"/>
<br />
<br />
The following (word) resulted in the most problems than any other part of the project. I began by creating two shares, HR and personal from Server Manager. In AD UC, I created two security groups to match the shares I created called HR, (not to be confused with the OU called HR I created prior) and Personal. I added john smith to both the HR and Personal shares. Within the shares, I removed the inherited permissions to have more control over them, and added the security groups to their respected share. To confirm the shares were created properly, within the Windows Sever in the C:\ drive, there a folder called Shares with the two shares I created. Right clicking on them and going to properties, then sharing, shows the network path for the share folder. This is where the headache begun.<br/>
<img src="https://github.com/user-attachments/assets/cc7eba89-98c7-4521-93b3-b0f26b01eca8" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/65ccc412-990a-4661-a383-30b19ff199d1" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/7eb54eae-83db-4923-8d70-6deac80e4a76" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/367b0b4c-f0da-4f55-99b0-3c49947bfe6c" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/330690cb-e1b9-4b17-afdd-4339f36a222e" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/a106f03b-b2de-481c-b9cf-3214b5df00f4" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/a6fbdce4-c27b-44d1-b7e1-f2895e2032a0" alt="Configuring Directory"/>
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
