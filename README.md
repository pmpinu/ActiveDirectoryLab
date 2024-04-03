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
Once installation of VMware Tools is finished, restart your virtual machine and log back in. In our initial virtual machine configuration, we assigned an additional virtual NIC (Ethernet1). In this step, we're going to assign it an IP address by opening up the properties of Ethernet1 and then navigating to the properties of TCP/IPv4. Ethernet0 will be internet-facing while Ethernet1 will be our internal network adapter. Since we will be using Windows Server itself as a DNS server, we can assign loopback IP for our DNS</i>:  <br/>
<img src="https://imgur.com/fHigGFZ.png" height="80%" width="80%" alt="NIC configuration"/>
 <br />
<br />
In the next step, we're going to rename our PC. You can navigate to windows search and type in "rename" to navigate to system settings</i>:  <br/>
<img src="https://imgur.com/73CvQ9Z.png" height="80%" width="80%" alt="Rename pc"/>
 <br />
<br />
Open the explorer and select the mounted drive and run <i>setup64</i>:  <br/>
<img src="https://imgur.com/1qs47Bt.png" height="80%" width="80%" alt="VMware Tools"/>
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
