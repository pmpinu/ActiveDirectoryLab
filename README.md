<h1>Active Directory Home Lab Tutorial</h1>


<h2>Description</h2>
This lab demonstrates how to install and configure an Active Directory inside of a virtual machine. We are going to be installing <b>Windows Server 2019</b> and <b>Windows 10</b> inside of a VMWare virtual machine. We will also be using PowerShell to add objects inside of a Domain.

<br/><b><i>***Core Active Directory Concept:</b> <br/>
- A Forest is a collection of Domains. <br/>
- A Domain is a collection of Objects.<br/>
- An Object refers to a user, group and/or a device.</i>
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>VMWare Workstation Player 17</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)
- <b>Windows Server 2019</b> (1748.rs5)

<h2>Lab walk-through:</h2>


<p align="center">
Configuring virtual machine settings for Windows Server 2019. Be sure to add an additional virtual network adapter: <br/>
<img src="https://imgur.com/ingdTGl.png" height="80%" width="80%" alt="Virtual Machine Settings"/>
<br />
<br />
Once you've launched the virtual machine, in the second step of the setup process, you will want to select one of the desktop experience options.:  <br/>
<img src="https://imgur.com/PJjxj97.png" height="80%" width="80%" alt="Windows Server 2019 setup"/>
<br />
<br />
Since we don't have an existing installtion of Windows Server 2019 on the disk space allocated to this virtual machine, we are going to select <i>Custom: Install Windows only (advanced)</i>: <br/>
<img src="https://imgur.com/dVv2dMG.png" height="80%" width="80%" alt="Windows Server 2019 setup, custom install"/>
<br />
<br />
Select the disk drive allocated to this virtual machine. This is the virtual disk drive Windows Server 2019 will be installed on:  <br/>
<img src="https://imgur.com/NeL1W3B.png" height="80%" width="80%" alt="Windows Server 2019 setup, select disk drive"/>
<br />
<br />
After installion steps have completed, you'll be presented with a screen to create a password for the admin account:  <br/>
<img src="https://imgur.com/GvJL7FB.png" height="80%" width="80%" alt="Admin password creation"/>
<br />
<br />
The next step will present you with a login screen. Enter the password you just created and then install VMware Tools by going to <i>File > Manage > Install VMware Tools</i>:  <br/>
<img src="https://imgur.com/HsgJ2S3.png" height="80%" width="80%" alt="Install VMware Tools"/>
<br />
<br />
Open the explorer and select the mounted drive and run <i>setup64</i>:  <br/>
<img src="https://imgur.com/1qs47Bt.png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br />
Keep the default selected options throughout the setup process:  <br/>
<img src="https://imgur.com/vdq0FJf.png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br />
Once installation of VMware Tools is finished, restart your virtual machine and log back in. In our initial virtual machine configuration, we assigned an additional virtual NIC (Ethernet1). In this step, we're going to assign it an IP address by opening up the properties of Ethernet1 and then navigating to the properties of TCP/IPv4. Ethernet0 will be internet-facing while Ethernet1 will be our internal network adapter. Since we will be using Windows Server itself as a DNS server, we can assign loopback IP for our DNS:  <br/>
<img src="https://imgur.com/fHigGFZ.png" height="80%" width="80%" alt="NIC configuration"/>
 <br />
<br />
In the next step, we're going to rename our PC. You can navigate to windows search and type in "rename" to navigate to system settings where we can rename our PC. I'm going to use "DC" for Domain Controller. Once you've renamed the PC, go ahead and restart your virtual machine:  <br/>
<img src="https://imgur.com/73CvQ9Z.png" height="80%" width="80%" alt="Rename pc"/>
 <br />
<br />
After your machine restarts, click on "Add roles and features" from the Server Manager Dashboard to begin the Active Directory Domain Service (AD DS) installation process. On the first window of the wizard, click Next:  <br/>
<img src="https://imgur.com/7ltvZde.png" height="80%" width="80%" alt="Adding roles and features"/>
 <br />
<br />
Select "Role-based or feature-based installation" then click Next:  <br/>
<img src="https://imgur.com/6Kss9Om.png" height="80%" width="80%" alt="Adding roles"/>
 <br />
<br />
 Select the DC:  <br/>
<img src="https://imgur.com/I40BAmN.png" height="80%" width="80%" alt="Adding roles"/>
 <br />
<br />
 Select "Active Directory Domain Services" then click next:  <br/>
<img src="https://imgur.com/rWlOi2v.png" height="80%" width="80%" alt="Adding roles"/>
 <br />
<br />
 On the confirmation window, select Install:  <br/>
<img src="https://imgur.com/fgBfe5e.png" height="80%" width="80%" alt="Install"/>
 <br />
<br />
  Once installation is complete, select "Promote this server to a domain controller" by clicking the yellow flag on the top right of the Server Manager Dashboard:  <br/>
<img src="https://imgur.com/pp56uQy.png" height="80%" width="80%" alt="Promote domain controller"/>
 <br />
<br />
  The AD DS Configuration Wizard should launch next. Select "Add a new forest" and name the root domain:  <br/>
<img src="https://imgur.com/C38oJRn.png" height="80%" width="80%" alt="add a new forest and root domain"/>
 <br />
<br />
  Create DSRM password:  <br/>
<img src="https://imgur.com/WTuyc23.png" height="80%" width="80%" alt="DSRM password"/>
 <br />
<br />
  Deselect "Create DNS delegation" then click next:  <br/>
<img src="https://imgur.com/nBbLe5K.png" height="80%" width="80%" alt="AD DS Configuration Wizard"/>
 <br />
<br />
   Once the NetBIOS domain name populates, click next:  <br/>
<img src="https://imgur.com/AuNC3ib.png" height="80%" width="80%" alt="NetBIOS domain name"/>
 <br />
<br />
   Keep everything as is for Database locations then click next on subsequent screens:  <br/>
<img src="https://imgur.com/BF0juq1.png" height="80%" width="80%" alt="AD DS Database"/>
 <br />
<br />
   Click install:  <br/>
<img src="https://imgur.com/h8cYhlu.png" height="80%" width="80%" alt="Prerequisites check"/>
 <br />
<br />
   Once installation is complete, the Windows Server will restart to apply changes:  <br/>
<img src="https://imgur.com/tbUIDuI.png" height="80%" width="80%" alt="Restart"/>
 <br />
<br />
   Once restarted, you will see <root-domain-name>/Administrator, in my case, LABDOMAIN/Administrator. Login:  <br/>
<img src="https://imgur.com/KBtEqkJ.png" height="80%" width="80%" alt="Login to root domain"/>
 <br />
<br />
Create a dedicated domian admin account instead of a built in admin account. Go to <i>Start > Windows Administrative Tools > Active Directory Users and Computers</i>. Then create an Organizational Unit and name it _ADMINS:  <br/>
<img src="https://imgur.com/DDyerYE.png" height="80%" width="80%" alt="Dedicated admin user in OU"/>
 <br />
<br />
<img src="https://imgur.com/HBfoCj9.png" height="80%" width="80%" alt="Dedicated admin user in OU"/>
 <br />
<br />
Now let's create a new user inside of our new OU and give the user an identity and a password. Then click finish:  <br/>
<img src="https://imgur.com/3hyqmOk.png" height="80%" width="80%" alt="Create user in _ADMIN OU"/>
 <br />
<br />
<img src="https://imgur.com/yig7LmN.png" height="80%" width="80%" alt="Create user in _ADMIN OU"/>
 <br />
<br />
<img src="https://imgur.com/K1EW76U.png" height="80%" width="80%" alt="Create user in _ADMIN OU"/>
 <br />
<br /> 
We still need to add Jane Doe as an admin user. Right-click on the user's name, select <i>properties</i> then navigate to the <i>Member Of</i> tab, then select <i>Add</i>. Then enter "Domain Admins" and click <i>Check Names</i>. Then select <i>Ok > Apply > Ok </i>:  <br/>
<img src="https://imgur.com/VeFcMWn.png" height="80%" width="80%" alt="Domain Admin"/>
 <br />
<br /> 
Now we're going to login with the dedicated admin user we just created. So logout then select "Other User" on the bottom left corner of the login screen and enter credentials. Once you're logged in, open up the command prompt to confirm you're logged in as the newly created user:  <br/>
<img src="https://imgur.com/VgXLi7E.png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
Since our Windows 10 VM will also be using an internal NIC, let's configure NAT so that it can have internet access. On the Server Manager dashboard, click on Add roles and features, then click Next, make sure "Role-based or feature-based installation" is selected, click Next:  <br/>
<img src="https://imgur.com/GoxTpVM.png" height="80%" width="80%" alt=""/>
 <br />
<br /> 
<img src="https://imgur.com/CylsY1F.png" height="80%" width="80%" alt=""/>
 <br />
<br /> 
Select Remote Access:  <br/>
<img src="https://imgur.com/GSuxDE9.png" height="80%" width="80%" alt="Remote Access"/>
 <br />
<br /> 
Select Routing, then proceed to install with default options on the subsequent stages. Once install completes, close the window:  <br/>
<img src="https://imgur.com/Octf8lZ.png" height="80%" width="80%" alt="Routing and Install"/>
 <br />
<br /> 
<img src="https://imgur.com/VPBJCLO.png" height="80%" width="80%" alt=""/>
 <br />
<br /> 
To configure Routing, navigate to "Tools" on the top right menu of the Server Manager Dashboard, select "Routing and Remote Access":  <br/>
<img src="https://imgur.com/XerLCgE.png" height="80%" width="80%" alt="Configure routing"/>
 <br />
<br /> 
Select configure option on the DC by right clicking on it:  <br/>
<img src="https://imgur.com/D0ferBz.png" height="80%" width="80%" alt=""/>
 <br />
<br /> 
Select NAT:  <br/>
<img src="https://imgur.com/hJTLjnD.png" height="80%" width="80%" alt="Select NAT"/>
 <br />
<br /> 
Select our internet facing adapter then proceed to install:  <br/>
<img src="https://imgur.com/qFx5yzA.png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
Our internet facing NIC is assigned an IP address by the DHCP server running on the router. For our internal client that we'll be installing (Windows 10), we will install a DHCP server on our domain controller so that IPs can be assigned to inetrnal clients. Navigate to "Add roles and features" and install DHCP server:  <br/>
<img src="https://imgur.com/D9YhUb1.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
 Once DHCP server is installed, go to the DHCP setting by selecting "DHCP" from the "Tools" menu on the top right. We need to tell the DHCP server whichi IP addresses it's allowed to assign to hosts. Right-click on "IPv4" and select "New Scope". For the name, I'm putting in a subset of usable host range IPs 192.168.3.10 - 100, then enter the range and subnet mask. The default gateway is going to be the DC internal NIC IP:<br/>
<img src="https://imgur.com/LJCIt6z.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
<img src="https://imgur.com/D6JMQkg.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
<img src="https://imgur.com/jlKsN2L.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br />
Keep the parent domain name as is. Keep defaults in the next steps then activate scope and finish the process:<br/>
<img src="https://imgur.com/ieHczsY.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
In the next step, right-click on the domain and select "Authorize" and then repeat and select "Refresh". The changes should reflect as shown:<br/>
<img src="https://imgur.com/z0eLvdW.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
<img src="https://imgur.com/Y4qWOkg.png" height="80%" width="80%" alt="DHCP"/>
 <br />
<br /> 
In the next steps, I'm using a PowerShell script in order to automate the user creation process:<br/>
<img src="https://imgur.com/5AVlPQC.png" height="80%" width="80%" alt="PowerShell User Creation Script"/>
 <br />
<br /> 
<img src="https://imgur.com/hxEYheB.png" height="80%" width="80%" alt="Automation with PowerShell ISE"/>
 <br />
<br /> 
In the next steps, create a new virtual machine and install Windows 10. You will want to set your network adapter to the Custom VMnet0 so that this VM will be on the same internal subnet as the domain controller. On the login screen, create a user and once you are on the desktop, you can check to confirm that DC DHCP server has assigned the windows client an IP within the range we specified earlier:<br/>
<img src="https://imgur.com/028BnJ9.png" height="80%" width="80%" alt="Windows 10 Client up"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
 Open the explorer and select the mounted drive and run:  <br/>
<img src=".png" height="80%" width="80%" alt="VMware Tools"/>
 <br />
<br /> 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
