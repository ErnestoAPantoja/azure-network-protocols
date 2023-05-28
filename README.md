<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this lab, I observe different kinds of network traffic to and from Azure virtual machines with Wireshark as well as experiment with network security groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 20.04

<h2>The Set-Up</h2>

Within Azure, I created two VMs within the same virtual network to ensure that they are able to communicate with each other. One VM will have Windows 10 Pro while the other uses Ubuntu. The Windows VM will connect to the other via the command line/PowerShell. 

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DutP0XT.png" height="80%" width="80%" alt="Azure Networking Steps"/>
</p>
<p>
Using Remote Desktop Connection, I connect to the Windows VM using its public IP address. From there, I installed Wireshark in order to begin inspecting traffic. 
</p>
<br />

<p>
<img src="https://i.imgur.com/2JQawfN.png" height="80%" width="80%" alt="Azure Networking Steps"/>
</p>
<p>
Within Wireshark, I filtered for ICMP (Internet Control Message Protocol) traffic and opened PowerShell to execute a command ping. Ping utilizes ICMP, which is used by devices in a network to communicate problems within data transmition. I used ping to see if I can communicate with the Ubuntu VM using its private IP address and with google.com. Afterwards, I used a perpetual ping to the Ubuntu VM in order to see how network security groups work. I executed the perpetual ping with the command: ping -t (ip address).
</p>
<br />

<p>
<img src="https://i.imgur.com/HTga2Iq.png" height="80%" width="80%" alt="Azure Networking Steps"/>
</p>
<p>
Within the Azure portal, I opened the networking settings for the Ubuntu VM and added an inbound security rule to block ICMP traffic. I make sure to have the priority higher than SSH (300) to ensure the rule applies first. 
</p>
<br />
