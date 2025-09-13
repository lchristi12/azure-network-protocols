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

- Create Virtual Machine
- Create Resource Group
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p> First, we are going to create a resourse group in the Azure portal using the free subscripiton.
  Name your resource group but for this tutorial, name it RG-Network-Activities. For the region, use East US 2. Make sure you use the same region when creating the Vitual Machine (VM). Then click review and create.
  
<img width="800" height="904" alt="Screenshot 2025-09-04 003818" src="https://github.com/user-attachments/assets/b08e9dbc-eff0-4aba-9e95-a5ddb40c7cc5" />

</p>
<p>
Next we create our VM. Click on create--> make sure you are on the correct subscription--> select the resource group that was created--> name the VM, windows-vm--> East US 2--> for image, select Windows 10 Pro version 22H2- x64 Gen2--> size select Standard _D2s_v3- 2 vcpus 8 GiB memory--> under Administrator account create username and password (use a notepad to keep track)--> make sure you check the box for the liscensing--> next for disk--> next for networking.

  Under Networking, we are going to create a Virtual Network. Click create new--> name the virtual network (for this tutorial, Lab2-Vnet) and click OK--> then click review and create.
<img width="800" height="793" alt="Screenshot 2025-09-04 004634" src="https://github.com/user-attachments/assets/897372e9-638b-4258-8de8-c6c8de4cb814" />
<img width="600" height="846" alt="Screenshot 2025-09-04 004728" src="https://github.com/user-attachments/assets/177d90aa-4d28-43f5-a5a6-61cb1b007dc0" />
<img width="1894" height="1288" alt="Screenshot 2025-09-04 004939" src="https://github.com/user-attachments/assets/c33613f7-667f-4bc7-a4d1-498e3a97106b" />

<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
