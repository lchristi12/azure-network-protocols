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

- Windows 10 Pro version 22H2- x64 Gen2
- Ubuntu Server 22.04 LTS-x64 Gen2

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

<p> Next we are going to create a Linux VM. Under the VM, click create--> resource group choose  RG-Network-Activities--> name for VM ( for this tutorial, linux-vm)--> image, Ubuntu Server 22.04 LTS-x64 Gen2--> size, Standard _D2s_v3- 2 vcpus 8 GiB memory--> Administrator account under Authentication type, choose password then create your own username and passowrd--> next for disk   --> next for networking--> virtual network, make sure its the one that was created (Lab2-Vnet). When you get to this part and Lab2-Vnet does not appear there, refresh and enter the information again and it should appear there--> click review and create.
<img width="900" height="823" alt="Screenshot 2025-09-04 005644" src="https://github.com/user-attachments/assets/271b18d2-ff15-48aa-9dba-66a377e402cf" />
<img width="900" height="830" alt="Screenshot 2025-09-04 005730" src="https://github.com/user-attachments/assets/b9669fc2-d25c-4cd2-8b72-aee2d9306094" />
<img width="1172" height="1116" alt="Screenshot 2025-09-04 010202" src="https://github.com/user-attachments/assets/540185aa-aa24-410c-b7f9-574c4d5fc19b" />

</p>
<p>
For this part, we are going to use the Remote Desktop Connection program to log in the Windows VM. Locate the IP address by either scrolling to the right on the VM page on Azure or clicking on the VM itself and locating the IP address there as well.
  Under the Remote Desktop Connection, enter the IP address and click connect--> enter username and password that you created--> A pop up should appear (For Windows) and click OK and you should get connected to VM.
<img width="1938" height="646" alt="Screenshot 2025-09-05 002225" src="https://github.com/user-attachments/assets/69d5ef0c-a0b3-451d-95b9-bf8fd0e5dad6" />
<img width="1536" height="844" alt="Screenshot 2025-09-05 002915" src="https://github.com/user-attachments/assets/e96061b7-4928-4510-bd2c-46748d9efaae" />
<img width="2000" height="1124" alt="Annotation 2025-08-31 002901" src="https://github.com/user-attachments/assets/4966571d-1060-4321-884a-09f2a5838448" />

<br />

<p> Once you are connected to the VM, install the program WireShark (https://www.wireshark.org) and select Windows x64 Installer. Follow the pop up prompts for installation.
<img width="1850" height="872" alt="Annotation 2025-09-05 043313" src="https://github.com/user-attachments/assets/be7ec5d6-7d56-44a0-8552-3df93cbb294e" />

</p>
<p>
Next, open Wireshark. You can search Wireshark in the serach bar at the bottom of the screen near the windows icon--> Click ethernet and in the top left corner, click the shark fin icon--> Once opened, you will see all the traffic constantly being generated.

<img width="1502" height="1156" alt="Annotation 2025-09-05 044039" src="https://github.com/user-attachments/assets/ebc24dd6-186b-48bc-aed2-f7860bae6524" />

</p>
<p> We are going to observe ICMP traffic.

  
First, go retrieve the private IP address from the linux VM (10.0.0.5)--> open Powershell in the Windows VM--> from the Windows VM, we are going to attempt to ping the linux VM. In Powershell, next to PS C:\user\(username)> type ping 10.0.0.5 and hit enter. Observe the traffice. Make sure to filter ICMP in wireshark. The next image shows a perpetual ping where it does not stop pinging. The command is PS C:\user\(username)> ping 10.0.0.5 -t

<img width="2192" height="1394" alt="Annotation 2025-09-05 044822" src="https://github.com/user-attachments/assets/563dabcd-fcf7-43ef-b1b7-085a2c564ea6" />
<img width="2184" height="1414" alt="Annotation 2025-09-05 045812" src="https://github.com/user-attachments/assets/f09ab6e8-fb51-4f54-a5d5-2792d80af7c0" />

</p>
<p> For this part, we are going to configure a firewall and going to tell it to block all incoming ping traffic from the Windows VM.

Go the VM page on the Azure Portal, click on the linux VM--> click on network--> network settings  --> Network Security Group, click linux-vm-nsg--> settings--> inbound security rules--> click +Add --> Source, Any--> Destination, Any--> service, custom--> Destination Port Ranges, leave asterisk  --> Protocol, ICMPv4--> Action, Deny--> Priority, 290--> make sure you enter a name or else it will not go through--> then click Add.

Once the rules are applied, go back to Powershell and observe what happens. The Pings will time out forever unless the rules is changed.

  
<img width="1904" height="874" alt="Screenshot 2025-09-05 010023" src="https://github.com/user-attachments/assets/6ff22a7c-9432-465c-94ed-ebfd7dbdea6d" />
<img width="1952" height="1248" alt="Screenshot 2025-09-05 010257" src="https://github.com/user-attachments/assets/bf3ed591-b2c3-4f29-b784-d8e7c32c177d" />
<img width="2194" height="1362" alt="Annotation 2025-09-05 050821" src="https://github.com/user-attachments/assets/5eaab00f-bdf3-430d-8dcd-18057ca5bec4" />

</p>We are going to observe SSH traffic




In WireShark,  make sure you filter SSH traffic--> open Poweshell 


Type--> SSH (username)@ private IP address of linux VM and observe the traffic.


<img width="2654" height="1394" alt="Annotation 2025-09-06 020215" src="https://github.com/user-attachments/assets/b74e9fdb-0832-44a3-b577-d9699b052dbe" />


<p> We are going to observe DHCP traffic

Filter DCHP--> in Powershell input ipconfig/ renew and observe the traffic.

  <img width="2552" height="1440" alt="Annotation 2025-09-06 021649" src="https://github.com/user-attachments/assets/1aab4484-b1f1-487d-861a-ae3924a4888f" />

<p> We are going to observe DNS traffic

In WireShark, filter DNS--> type nslookup www.disney.com and observe traffic

  <img width="2880" height="1548" alt="Annotation 2025-09-06 022740" src="https://github.com/user-attachments/assets/265050d5-60ed-4e4e-a236-ac6b73e49d1a" />

<p> We are going to observe RDP traffic

In WireShark, filter RDP and observe traffic. The tutorial we are doing right now is an example of RDP. We are remoting into a VM.

  <img width="2880" height="1392" alt="Annotation 2025-09-06 023236" src="https://github.com/user-attachments/assets/bbeeea5d-44ac-4a60-a0b6-35a59678f1b9" />


  This is the end of the tutorial. Hope this is helpful and do not forget to delete the VM once finished or else you will be charge money for them.

<br />
