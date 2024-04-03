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
Configuring virtual machine settings for Windows Server 2019: <br/>
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
<img src="https://imgur.com/GvJL7FB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
