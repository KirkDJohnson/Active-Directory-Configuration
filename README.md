<h1>Configuring and Troubleshooting Active Directory</h1>

<br />
<h2>Description</h2>
In this part of the project, with the previously installed Active Directory domain, I began expirementing with the different functionalities of Active Directory such as Group Policy Management and Security Groups as well troubleshooting common user issues from the help desk perspective. During the task of learning how to create shared drives I came accross a serious hickup that after much time and research I was able figure out the issue and overcome it.

<h2>Utilities Used</h2>

- <b>Sever Manager</b>
- <b>Active Directory Users and Computers (AD UC)</b>
- <b>Group Policy Management Editor</b>

<h2>Environments Used </h2>

- </b>Windows Sever 2022</b>
- </b>Windows 10 Pro</b>

<h2>Lab Overview:</h2>

<p align="center">
This picks right up from the previous repository, "Installing Active Directory". To summarize, I installed Windows Server 2022 and configured it to be the domain controller of the domain ADLab.local. I installed two Windows 10 Pro instances, and created two user accounts, helpdesk that has full administrator privileges and john smith with only base privileges. This repository serves two purposes. First, it showcases me experimenting with different Active Directory functions and second, I troubleshoot many common issues that users may experience that a helpdesk or IT support specialist may tasked with fixing.<br />
 <br />
 <br />
I first began experimenting with Organizational Units (OUs). In AD UC I created an OU called HR for Human Resources and under the Users Directory, I clicked and moved john smith into the new HR OU.<br/>
<img src="https://github.com/user-attachments/assets/be7b79c3-1e55-47ea-92e5-f89b83434490" alt="Configuring AD"/>
<br />
<br />
With the newly created OU, I now opened Group Policy Management, a critical part of Active Directory domain/user management. I decided to change a very important setting, "Account lockout threshold", which I found under Computer Configuration. Computer configurations differ from User configurations in that no matter the user that logged on, that policy is on the computer that is connected with the Domain Controller. I found the policy in security settings, and changed it to now lock the user out of their account after five incorrect password login attempts.<br/>
<img src="https://github.com/user-attachments/assets/3cc65960-0624-4550-9c53-c2ba1ede972b" alt="Configuring AD"/>
<img src="https://github.com/user-attachments/assets/8578e4d0-77a6-417d-879f-1b779bdbb25a" alt="Configuring Directory"/>
<br />
<br />
One of the most common problems with an account is that a user forgets their password and gets locked out of there account. I simulated this by inputting the wrong password when logging into john smith. On the helpdesk account or the domain controller itself, I could open AD UC, find john smith in the HR OU, double click on this account name and a window with many tabs opens. I first went to Account, and unlocked his account, and when right clicking his name there is a window that says reset password. The pop-up appeared also allowed me to unlock his account in addition to resetting his password. In this case, I created a temporary password, and checked the box that requires the user to change their password when logging in. This is crucial for security and aduiting because proper security principles state that only one user should know the password to an account. If the help desk worker know the password as well, they could log into john's account and potentially conduct malicious behavior and it would more difficult determining who it was. When john logs back in, the temporary password is already populated and he just needs to change his password now.<br/>
<img src="https://github.com/user-attachments/assets/3ec7feab-34b3-4e25-bd08-ffaee8e96122" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/884e8ca9-db28-4bc5-8928-de13e6849a6f" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/ed899abf-1a31-4fc9-b06c-e5babae66a76" alt="Configuring Directory"/>
<br />
<br />
In another troubleshooting scenario, when the user attempts to log in, they are presented with the message, "The user's account has expired." This would prevent them from logging in and likely result in them contacting helpdesk/IT support. To remedy this issue, I would once again use AD UC, and if I did not know where the user was located, I could right click on the domain, use the search feature, change filter to Entire Directory, and then input the user's name. Double clicking on the user and going to Account, at the bottom, you can change the account expiration to a future date or check the box that sets the account to never expire.<br/>
<img src="https://github.com/user-attachments/assets/c8f5f302-3863-4745-b05a-81610aa48732" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/e5456fdf-c93f-4235-9047-6c26ff011892" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/e8111255-7e74-451a-9804-ded4c68cce1d" alt="Configuring Directory"/>
<br />
<br />
Next, the issue and troubleshooting method is a bit more complex, maybe there is an easier way to go about it. A user is attempting to log in, and is met with the message, "The security database on the server does not have a computer account for this workstation trust relationship." Maybe an admin accidently deleted the computer from the computer group in AD UC. To solve this, I log in as a local user, in case the administrator by using ".\" to force the local authentication. I moved the computer off the domain into a workgroup and then back to the ADLab.local domain, restarted the computer and the computer re-joined the domain and can be seen in the Computers tab in AD UC.  <br/>
<img src="https://github.com/user-attachments/assets/e7890f71-cf0e-4431-862b-deb755fed507" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/6e2abe5e-2cab-447e-8b07-7d22131d38c4" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/940be1bc-7ff3-429f-b43d-61ecf7e8e6df" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/af876dcc-363b-422a-ae1b-8cc86934d547" alt="Configuring Directory"/>
<br />
<br />
The following task resulted in the most problems than any other part of the project. I began by creating two shares, HR and Personal from Server Manager. In AD UC, I created two security groups to match the shares I created called HR, (not to be confused with the OU called HR I created prior) and Personal. I added john smith to both the HR and Personal shares. Within the shares, I removed the inherited permissions to have more control over them, and added the security groups to their respected shares. To confirm the shares were created properly, within the Windows Sever in the C:\ drive, there a folder called Shares with the two shares I created. Right clicking on them and going to properties, then sharing, shows the network path for the share folder. This is where the headache begun.<br/>
<img src="https://github.com/user-attachments/assets/cc7eba89-98c7-4521-93b3-b0f26b01eca8" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/65ccc412-990a-4661-a383-30b19ff199d1" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/7eb54eae-83db-4923-8d70-6deac80e4a76" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/367b0b4c-f0da-4f55-99b0-3c49947bfe6c" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/330690cb-e1b9-4b17-afdd-4339f36a222e" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/a106f03b-b2de-481c-b9cf-3214b5df00f4" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/a6fbdce4-c27b-44d1-b7e1-f2895e2032a0" alt="Configuring Directory"/>
<br />
<br />
For the Personal share folder, I went to john's user account on AD UC, and under the profile tab, I changed his home folder from local path to the shared folder and that was successsful. However, my luck ended here. Because there was only one path I can link the share drive on through AD UC, I had to get john access to the HR share in a different way. The first thing I tried was on the Windows Server, I went to the HR share folder, went to properties, sharing, and clicked share. This opened a window that looked promising, I added john smith to it and clicked share. However, after logging into john's account I only saw the shared Personal drive and not HR.<br/>
<img src="https://github.com/user-attachments/assets/ee573fc0-dd9c-4b9a-8dff-d775a14eeb45" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/2b4a1633-195a-4035-92e3-60764c254d49" alt="Configuring Directory"/>
<br />
<br />
This now began the unintented troubleshooting process of sharing the HR drive with john. (I did not take many screen shots of this process as I was so focused on fixing it and researching.) On john's computer, when in file explorer, I tried typing "\\Windowssever202" as how it was shown and working with the "Personal" shared drive but nothing came up. I found a many great resources and steps to fix the issue online. The first thing I tried was to map the drive with the IP address of the Sever rather than the domain name, so I typed \\10.1.10.2\HR and to my suprise, it worked. I could have left it at that and been done but I knew that I can have work properly. Seeing that mapping the drive to the IP address worked but not the domain name led me to believe it was an issue with DNS on john's machine. So I went to command line and typed nslookup ADLab.local, and it output the correct IP address, 10.1.10.2, which was also suprising because it meant that DNS was working as far I know. However, the post mentioned a possible fix of going to IPv4 Advanced settings, where I statically assigned the layer 3 addresses, and append the domain in the DNS suffixes. This did not solve the issues. The next fix, mentioned that Network Discovery and File and Printer sharing had be on for the client and server. On john's computer they were set to off and I had no issue when setting then to on. However, when on the Windows Server I ran into further trouble. When I would switch Network Sharing to on, and click save, it would instantly be reverted to the off position. So after further research on Network Sharing I discovered that there were a few services that I needed to make sure were running, these included: DNS Client, Function Discovery Resource Publication, SSDP Discovery, abd UPnP Device Host. After enabling a few of these that were set to disabled, I was able to turn on Network Sharing and have it stay on. With that I tried the first step again of sharing the drive from the sharing tab in the HR folder, added john and it finally worked.<br/>
<img src="https://github.com/user-attachments/assets/f67243d2-71af-4ff2-8551-b87379b61bb4" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/2a43f95f-f28e-4423-979a-cca0f06084f1" alt="Configuring Directory"/>
<br />
<br />
I now began to expirement more with Group Policy Management. I right clicked on Group Policy Objects, selected new and labled the Group Policy Object (GPO) "Task Manager Setting".  Within the GPO, I opened the delegation tab, and added john smith to it, I think I could have added the HR OU but I was not sure so I just added john. I then right clicked the GPO and went to edit which opened the Group Policy Management Editor. Under User Configruation, Administrative Template, System, Ctrl+Alt+Del, I found the entry for "Remove Task Manager". Clicking on that option opened a window where can enable it as well as an explanation of what this policy does. I then clicked and moved the new GPO over the HR OU to tie them together.<br/>
<img src="https://github.com/user-attachments/assets/008e377a-61c8-45ac-8346-a69c0613815a" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/f12cc696-40e2-4ee9-bf21-8fef623291d2" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/e4810e2d-7ae8-4eb4-b5cf-6ea1e2894b51" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/dd29aee5-9266-4138-809f-2dcdd0917ea1" alt="Configuring Directory"/>
  <img src="https://github.com/user-attachments/assets/9d7fd540-9311-4e1f-ac3a-cf41f827e58d" alt="Configuring Directory"/>
<br />
<br />
To make this change happen, because it was at the user level, I could open the command line and use the command "gpupdate /force" which updates the User Policy. I believe if it was a Computer Policy change I would have had to restart the computer for it to take effect. I can confirm that this change was successful by right clicking on the toolbar at the bottom and seeing that Task Manager is grayed out meaning I cannot open it.<br/>
<img src="https://github.com/user-attachments/assets/74e9862b-4656-410d-95c6-4a606f2d638b" alt="Configuring Directory"/>
 <img src="https://github.com/user-attachments/assets/b05a61f2-321d-4ee9-a902-82ee9246b1a9" alt="Configuring Directory"/>
<br />
<br />




<h2>Thoughts</h2>
The part of the project I got great exposure and expirenece with different important aspects of Active Directory such as Group Policy Objects and sharing drives. However, with the share drives, this was a significant hurrdle to overcome but I was probably the part of the project where I have learned the most thus far. Though it took a very long time to fix, rather than already knowing how to "troubleshoot" a user's account by resetting their password, this was actual realtime unplanned troubleshooting and I am glad I figured it out. Due to Active Directory being so widely used, I found extensive information about fixing issues from the domain controller perspective which made the process easier than if I were in the dark. Overall, this part of the project was great as everything I did was new so there was lots of learning that took place. 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
