

<h1>Active Directory Home Lab</h1>

  <!--### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)
-->

<h2>Description</h2>
We will demonstrate how to set up an Oracle Virtual Box Active Directory Home Lab Environment in this lab. Running through this lab a few times, asking questions when things are unclear, and eventually attempting to construct it without watching will undoubtedly improve your comprehension of how Windows networking and active directory function.

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle Virtual Box</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Server 2019</b>

<h2>Program walk-through:</h2>

<p align="center">
Active Directory Network Diagram: <br/>
<img src=https://i.imgur.com/T0vWgC3.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Download Oracle VN Virtualbox with extension pack: <br/>
https://www.virtualbox.org/wiki/Downloads
<img src=https://imgur.com/MVgav8K.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Download Windows 10 ISO and Windows Server 2019 ISO: <br/>
https://www.microsoft.com/en-us/software-download/windows10ISO
https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
<br />
<br />
Create Domain Controller Virtual Machine and set version to other windows 64 bit: <br/>
<img src=https://imgur.com/9NV4qRp.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Set to bidirectional: <br/>
<img src=https://imgur.com/8dSRKs4.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under system tab set processor cores (recommended at least 2 cores to allocate): <br/>
<img src=https://imgur.com/Y3DCCNb.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under network tab set adapter 1 as NAT, enable adapter 2 and set as internal network: <br/>
<img src=https://imgur.com/Er2WB1l.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Launch VM, add Windows Server 2019 iso: <br/>
<img src=https://imgur.com/GrzB8Xe.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Installing Windows Server ISO, click standard edition desktop experience for a GUI: <br/>
<img src=https://imgur.com/7esawWA.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Custom install then press next: <br/>
<img src=https://imgur.com/igv5O4a.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Set password as Password1 for this lab to keep it simple: <br/>
<img src=https://imgur.com/9OsG7oM.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under devices click insert guest image for faster user experience: <br/>
<img src=https://imgur.com/suEba1v.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under file explorer click this pc, then click virtualbox guest addition, then run and install the executable that ends in amd64, reboot and shut VM down: <br/>
<img src=https://imgur.com/Vtj1JUh.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<img src=https://imgur.com/ASFqsVo.png" height="80%" width="80%"
<br />
<br />
Click network, change adapter options, rename the networks, Internet (click status and see which network has an ipv4 address to find out which is connected to internet), and Internal: <br/>
<img src=https://imgur.com/6GhHZpk.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <img src=https://imgur.com/7zA4zAk.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <img src=https://imgur.com/AAtnU9l.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under Internal network properties click internet protocol version 4 and assign the ip address 172.16.0.1 with subnet mask of 255.255.0.0 and use lookback address of dns server 127.0.0.1:  <br/>
<img src=https://imgur.com/Tuxi5Zs.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Right click start menu, go to system, rename this pc to DC then reboot:  <br/>
<img src=https://imgur.com/Zuf5Khx.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Add domain service, click add roles and features and press next until the active directory domain services checkbox becomes available, click on it and add feature, install:  <br/>
<img src=https://imgur.com/sdUGJ0b.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<img src=https://imgur.com/pugZoQU.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Promote this server to domain controller, add new forest named mydomain.com press next and make up simple password like Password1, keep pressing next until install, reboot:  <br/>
<img src=https://imgur.com/0yyUpG0.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<img src=https://imgur.com/iOmYuoq.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Under start menu click on active directory users and computers, right click mydomain.com, click new, then organizational unit for admin accounts, name it _ADMINS uncheck prevent accidental deletion:  <br/>
<img src=https://imgur.com/Fi1gEiE.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<img src=https://imgur.com/Cq243CN.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Create new admin user acccount under _ADMINS organizational Unit use Password1 as password and check password never expires for this lab:  <br/>
<img src=https://imgur.com/7K3RGUC.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Right click on new user and click properties, go to member of tab, press add, type in domain admins and resolve name press apply and ok:  <br/>
<img src=https://imgur.com/tQxb8QX.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Sign out, and log in to new admin account using your name you created. Mine was a-ncalderon:  <br/>
<img src=https://imgur.com/ktJypmN.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Going to install RAS/NAT next for remote access, allowing server to be on virtual private network but still access internet through domain controller:  <br/>
 <img src=https://imgur.com/9XsA7RT.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
On server manager, add roles and features again, but check the box remote access instead, press next and then check the routing box, next until install:  <br/>
 <img src=https://imgur.com/d7CfF82.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Top right of server manager is an option for tools, click the drop down menu and find routing and remote access option:  <br/>
 <img src=https://imgur.com/9XsA7RT.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Right click DC and configure routing and remote access, click the NAT network option, click the internet interface and click next then finish:  <br/>
 <img src=https://imgur.com/ZMvkoy7.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <img src=https://imgur.com/Bw1sgIv.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <img src=https://imgur.com/KiH7KXA.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Add roles and features again, click dhcp role next and install:  <br/>
 <img src=https://imgur.com/K9h6QsK.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Click tools drop down on server manager and find dhcp, create new scope by right clicking ipv4, name the scope our range of 172.16.0.100-200, press next, set start ip as 172.16.0.100 end as 172.16.0.200, length as 24 and press next until router(default gateway) screen, type the domain controller's ip address of 172.16.0.1 and press add click next until finish:  <br/>
 <img src=https://imgur.com/YfQ4jG0.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <img src=https://imgur.com/XMnHqfi.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
 Right click mydomain.com folder, click authorize and refresh:  <br/>
 <img src=https://imgur.com/xVpAsj7.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Open new user powershell script to create 1000 users, paste link to internet explorer sacve as, put on desktop, extract file: <br/>
 https://github.com/joshmadakor1/AD_PS/archive/master.zip <br/>
 <img src=https://imgur.com/ahIHJf9.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Open names file from the script file, add your name on top of the list of names, save file
<br />
<br />
Run powershell ISE run as admin:  <br/>
 <img src=https://imgur.com/1hfssaK.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Click open, find the create_users file from the AD_PS-master folder, open script:  <br/>
 <img src=https://imgur.com/ut4Vbi0.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
In the command prompt type "Set_ExecutionPolicy unrestricted" yes to all <br />
 <br />
:  <br/>
 <img src=https://imgur.com/1hfssaK.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Navigate to the directory of AD_PS-master file by typing in the command line "cd C:\users\a-ncalderon\desktop\ad_PS-master", substituting your username instead, click play on script to create all the accounts: <br/>
<img src=https://imgur.com/7fm7bY9.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Create the client Windows 10 virtual machine with virtualbox, allocate at least 2 processor cores, and 2 gigs of RAM, set clipboard and drag n drop to bidirectional like last VM: <br/>
<img src=https://imgur.com/ycOBEnL.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Set network tab to internal network as adapter 1: <br />
 <img src=https://imgur.com/kWp0YLG.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
 Open Client VM, start with windows 10 ISO, join with windows 10 pro, custom install: <br />
<img src=https://imgur.com/oUTW5qy.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
:
<img src=https://imgur.com/oUTW5qy.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
 Log on to windows 10 VM, open cmd, type ipconfig, if you have a default gateway, it worked! <br />
<img src=https://imgur.com/Gbo4V3b.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
 : <br />
<img src=https://imgur.com/Gbo4V3b.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
type ping google.com in CMD, if it works then DNS server is working <br />
<br />
Right click start menu and go to system, scroll down, click rename this pc advanced: <br />
<img src=https://imgur.com/mI5e6PH.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
<br />
<br />
Click change and rename to CLIENT1, type in domain of mydomain.com to join the domain at same time: <br />
<img src=https://imgur.com/CVMccn1.png" height="80%" width="80%" alt="Active Directory Home Lab steps"/>
 <br />
 <br />
 DONE!! You created a fully functional active directory server, essentially a basic mini corporate network.
 
 <!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
