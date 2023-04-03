<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
Observing various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

- Step 1: Create 2 VMs, one with a Windows 10 operating system and the other with a Linux Ubuntu operating system.
- Step 2: Install Wireshark on VM #1, run it, and filter for ICMP traffic only.
- Step 3: Retrieve VM #2's private IP address and ping it from VM#1's Command-Line.
- Step 4: Observe different types of traffic between VM#1 and VM#2 (SSH, DHCP, DNS, and RDP) using CMD and WireShark.

<h2>Actions and Observations</h2>

<p>
<img src="https://i.ibb.co/D5wSscF/Lab2-1.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.ibb.co/8gD9dyQ/Lab2-3.png" height="70%" width="70%" alt=""/>
</p>
<p>
1. The first thing I did was create a new resource group in Azure. I then created 2 VMs in that resource group, one with a Windows 10 operating system and the other with a Linux operating system. The Windows VM is named VM1 and the Linxus VM is named VM2.
</p>
<br />

<p>
<img src="https://i.ibb.co/mD78pKS/lab2-4.png" height="70%" width="70%" alt=""/>
</p>
<p>
2. Next, I installed WireShark on VM1, ran it, and filtered for ICMP traffic only. Then, I retrieved VM2's private IP address and pinged it from VM1's command-line. This allowed me to observe requests and replies between the 2 VMs within WireShark.
</p>
<br />

<p>
<img src="https://i.ibb.co/BZrRKf3/lab2-6.png" height="70%" width="70%" alt=""/>
</p>
<p>
<img src="https://i.ibb.co/tMbpmNw/lab2-7.png" height="70%" width="70%" alt=""/>
</p>
<p>
3. Then, I went back into Azure and changed VM2's "Inbound Security Rules" to deny any ICMP traffic. After pinging VM2 again I began to see timeout messages. In WireShark there were only requests and no replies. I then went back into Azure and allowed ICMP traffic once again.
</p>
<br />

<p>
<img src="https://i.ibb.co/GHf2XPP/lab2-9.png" height="70%" width="70%" alt=""/>
</p>
<p>
4. Next, I tested for SSH traffic. In WireShark I filtered for SSH traffic and connected to VM2 with SSH in the command-line. After connecting I begin to see plenty of traffic. I then ran a few Linux commands and saw more traffic.
</p>
<br />

<p>
<img src="https://i.ibb.co/rMrf37s/lab2-10.png" height="70%" width="70%" alt=""/>
</p>
<p>
5. Next, I filtered for DHCP traffic. In the command-line I typed (ipconfig /renew) to attempt to issue a new IP address for VM1. I then began to see traffic come through.
</p>
<br />

<p>
<img src="https://i.ibb.co/kXXc4Xj/lab2-11.png" height="70%" width="70%" alt=""/>
</p>
<p>
6. Next, I filtered for DNS traffic. In the command-line I typed (nslookup www.google.com) to find google's IP address. Plenty of traffic came through. 
</p>
<br />

<p>
<img src="https://i.ibb.co/XzkM1MZ/lab2-12.png" height="70%" width="70%" alt=""/>
</p>
<p>
7. Lastly, I filtered for RDP traffic. Due to RDP being used to connect my host computer and the VM, I began to see non-stop traffic in WireShark.
</p>
<br />
