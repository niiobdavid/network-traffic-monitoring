<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>

In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. 
You can follow along with this [Lab Checklist](https://docs.google.com/document/d/1Oo12HvS5CaRz5E8iPQFOMprqiz-dBTPoYLjNTuSuvHk/edit?usp=sharing)
<br />

![image](https://github.com/user-attachments/assets/e8539e70-0495-455e-95b7-5541d650ecce)


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups]([https://www.youtube.com](https://youtu.be/6wVA8zzBlHA))

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

- Create our Virtual Machines
- Observe ICMP Traffic
- Configuring a Firewall [Network Security Group]
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
- Lab Cleanup (DON’T FORGET THIS)

<h2>Project Walk-through:</h2>

<h3>Create our Virtual Machines:</h3>

<p>
Navigate to Microsoft Azure and create a resource group:
</p>
<br/>

<p> 
  <img src="https://i.imgur.com/hRSFxQ0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>  

<br />
 
<p>
Create an "Azure Virtual Machine" with windows
</p>
<br />

<p>
  <img src="https://i.imgur.com/uxTTe2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/FSinXjs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/70EFeI5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/oXfJghd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/PU2D3fE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/IsiAubG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/euUTEYI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/PAT78N7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Create another "Azure Virtual Machine" with linux
</p>

<p>
  <img src="https://i.imgur.com/uxTTe2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/wASK6Fk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/HiucPjg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/PCSnxY1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/x7xBGb4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/RsB7X4i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Make sure both VMs are on the same Virtual network
</p>

<p>
  <img src="https://i.imgur.com/Q9RKRXa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/QQJt0by.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Connect  to the Windows VM
</p>

<p>
  <img src="https://i.imgur.com/Z4WKuMv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/P8FsV6K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/p3Gz1Hb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/Et0zmtY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/yDbyNhr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/on5DI68.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Observe ICMP Traffic</h2>

<p>
Within your Windows 10 Virtual Machine, Install Wireshark
</p>

<p>
  <img src="https://i.imgur.com/flwye37.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/dDvdYFC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/2CUnOVf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/67OP3ts.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/VqT0hg5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/crlZyrw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/0Q4Iekk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/JSK8HGe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Open Wireshark and start packet capture
</p>

<p>
  <img src="https://i.imgur.com/outX1WZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/Pp1GACZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/qJqfMrl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Within Wireshark, filter for ICMP traffic only
</p>

<p>
  <img src="https://i.imgur.com/UwW1qyN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/ooIB7oJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
</p>

<p>
  <img src="https://i.imgur.com/ezLhWz4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/K6yKXRU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/cD8wGDj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Observe ping requests and replies within WireShark
</p>

<p>
  <img src="https://i.imgur.com/wTd3AlI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
</p>

<p>
  <img src="https://i.imgur.com/nyJJK8n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
</p>

<p>
  <img src="https://i.imgur.com/NwttOt5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/RYxq7ON.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Configuring a Firewall [Network Security Group]</h2>

<p>
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
</p>

<p>
  <img src="https://i.imgur.com/sWuwVVf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/dvIb5XE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/UNcdgLe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
</p>

<p>
  <img src="https://i.imgur.com/YSb9szu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM
</p>

<p>
  <img src="https://i.imgur.com/cL3g1S5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/hJJtEnU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
</p>

<p>
  <img src="https://i.imgur.com/Qk8IRxZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p>
Stop the ping activity
</p>

<p>
  <img src="https://i.imgur.com/Z2aUdrj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Observe SSH Traffic</h2>

<p>
Back in Wireshark, Filter for SSH traffic only
</p>

<p>
  <img src="https://i.imgur.com/mlVSt9w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
</p>
<p>
Open PowerShell, and type: ssh labuser@<private IP address>
</p>
  
<p>
  <img src="https://i.imgur.com/Zcdh2rV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
</p>

<p>
  <img src="https://i.imgur.com/LuB0haQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Exit the SSH connection by typing ‘exit’ and pressing [Enter]
</p>

<p>
  <img src="https://i.imgur.com/6BkyRNA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Observe DHCP Traffic</h2>

<p>
Back in Wireshark, filter for DHCP traffic only. 
</p>
<p>
Create a text file. Type "ipconfig /release , ipconfig /renew" and Save as "dhcp.bat" under "All Files" in the directory C:\ProgramData
</p>

<p>
  <img src="https://i.imgur.com/InQNrwr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line
</p>

<p>
  <img src="https://i.imgur.com/t3bwTuF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Open PowerShell as admin and run: the .bat file
</p>

<p>
  <img src="https://i.imgur.com/yZj6NQ4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/ovYtVms.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Observe the DHCP traffic appearing in WireShark
</p>

<p>
  <img src="https://i.imgur.com/VWYe8jY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Observe DNS Traffic</h2>


<p>
Back in Wireshark, filter for DNS traffic only
</p>
<p>
From Powershell, use nslookup to see what google.com and disney.com’s IP addresses are and observe the DNS traffic being show in WireShark
</p>
<p>
  <img src="https://i.imgur.com/2mzJ5H8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/Hmgv7Q0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Observe RDP Traffic</h2>

<p>
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389) and observe the immediate non-stop spam of traffic
</p>
<p>
It’s non-stop spamming because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
</p>

<p>
  <img src="https://i.imgur.com/3fgH5B9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />


<h2>Lab Cleanup (DON’T FORGET THIS) </h2>

<p>
Close your Remote Desktop connection and Delete the Resource Group(s) created at the beginning of this lab
</p>

<p>
  <img src="https://i.imgur.com/WVXrKm7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/3zYTXeb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Verify Resource Group Deletion
</p>

<p>
  <img src="https://i.imgur.com/fnuocR9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/6IN1uqW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Congratulations, You completed this Lab
</p>
