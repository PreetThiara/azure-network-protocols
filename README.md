<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- This tutorail requires the use of the virtual machines from the last tutorial
- Create some sample file shares and assign permission
- Test access

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/lOfij16.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1 go to the c drive -> create 4 folders -> "read-access", "write-access", "no-access", "accounting". 
<p>
<img src="https://i.imgur.com/drbk5Aa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/hu5eSuX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click on read-access -> properties -> sharing -> domain users -> add -> In Permission level field can toggle the permission to give to the users.
Assign following permissions for the folders: "read access" -> Group Domain users -> Permission=read "Write access" -> Group Domain Users -> Permission=read/write "no access" -> Group Domain Users -> Permissions= "read/write Skip accounting for now
</p>
<img src="https://i.imgur.com/uDwdNvY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uMP3KGF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/VEWCJyh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to active directory on DC-1 -> New Organizational Unit named Security Groups. In that unit create new group called Accountants. Go to c drive -> accounting folder -> Add "Accountants" -> Permissions will be read/write. To give users access to that folder right click on accountants folder -> members -> Add "domain users" for everyone to have access or the user that will have access to the folder
</p>
<img src="https://i.imgur.com/AhdH6or.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to folders -> Type in \\DC-1 on top -> Test different type of accesses to the folders 
