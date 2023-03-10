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

- Create Resources in Azure
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

- Create a Resources Group in Azure
  - Create a Virtual Machine with Windows 10 and 2 virtual cpus  (VM1)
  - Create a Virtual Machine with Linux (Ubuntu) and 2virtual cpus  (VM2)
- Remote desktop into VM1, download and install Wireshark

<p>
<img src="https://i.imgur.com/vyCJKBs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Open WireShark and click on the blue fin in the top left hand corner and you will see all diferent kinds of traffic appear. 

</p>
<br />

<p>
<img src="https://i.imgur.com/g6IflCD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Filter for ICMP traffic only by typing "ICMP" in the filter bar. Notice that the traffic being displayed is only ICMP traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/uqr8ncW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  -  Get the private IP address from the Ubuntu VM (VM2)
     - Go back to VM1 open the CMD window and ping the private IP address for VM2
     -Within WireShark observe the ping requests and replies between the 2 virtual machines
</p>
<br />

<p>
<img src="https://i.imgur.com/Hz1yllM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

-  From the VM1 ping the public website www.google.com and observe the traffic in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/kdhLWCK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

-  Now we are going to observe SSH traffic.
   - Filter SSH for SSH Traffic only in WireShark.
   - From VM1 SSH into VM2 by typing in the CMD line "SSH Labuser@10.0.0.5" 
   - Enter the password for VM2 when promted You will be promted.
   - In WireShark you will instantly see the traffic between the 2 VMs.
</p>
<br />

<p>
<img src="https://i.imgur.com/dIuVnbv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

-  Now we will observe DHCP Traffic (Dynamic Host Configuration Protocol). This protocol operates on ports 67 and 68. Its primary function is to assign different devices their IP-Address. We will issue a new IP address for our Windows 10 VM (VM1).
   - Filter for DHCP traffic only in WireShark
   - From the CMD line in VM1 type "IPCONIG/RENEW"
   - Observe and inspect the traffic in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/F8ePtKt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

-  Observe DNS Traffic
   - Filter for DNS Traffic only in WireShark
   - In the CMD line type in the command "nslookup" www.google.com
   - Inspect traffic in WireShark you will see the public IP address for the www.google.com
</p>
<br />

<p>
<img src="https://i.imgur.com/wbLMkoc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Observe RDP Traffic
  - To filter for RDP Traffic only we can enter "tcp.port==3389" in WireShark
  - Notice that there is a lot of traffic as we are currently in a Remote Desktop Session
  
</p>
<br />

<p>
<img src="https://i.imgur.com/apH8A52.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- In this lab you were able to inspect the various types of Protocol traffic used between Virtual Machines on a network. In addition how 
  to utilize the tool WireShark for indepth traffic detail which can be utilized for troubleshooting various type of network issues.
