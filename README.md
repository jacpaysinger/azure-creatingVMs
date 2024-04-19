<p align="center">
<a href= "https://ibb.co/JcgmV4N"><img src="https://i.ibb.co/mRgbkwm/Untitled.png" alt="Untitled" border="0"></a>
</p>

<h1>Creating Virtual Machines (Windows and Linux) in Microsoft Azure; and Configuring NSGs. </h1>
In this project, I'll demonstrate how to create two separate virtual machines in Microsoft Azure. I'll show how to configure the Network Security Groups (NSG) to allow all web traffic to prepare the VMs for our honeypot. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04


  <br/>

<h2> Creating Virtual Machines: High-Level Steps</h2>

- Step 1 Create an Azure account (tenant) and Subscription
- Step 2 Create a VM running a Windows Server
- Step 3 Create a VM running a Linux Server
  

<h2>Actions and Observations</h2>
<p>
<a href="https://ibb.co/3N9HbwG"><img src="https://i.ibb.co/Phv8yR3/Untitled-2.png" alt="Untitled-2" border="0"></a>

</p>
<p>
After creating an account and subcription, create a new VM by searching VM > select VM > select create Azure VM. From the "Create a Virtual Machine Page" select "create new" under Resource Group to create a new Resource Group for your VM to run under. Name your resource group "RG-Cyber-Lab" for the purpose of this tutorial. Next, name your virtual machine "window-vm" and select (US) East US 2 as your region. After naming the VM and placing it in the proper region, select the Operating System under Image. For this VM we will be using Windows 10 Pro verison 22HZ - x64 Gen2. 
</p>
<br />
<p>
<a href="https://ibb.co/37DLyXP"><img src="https://i.ibb.co/L8L2zws/Untitled2.png" alt="Untitled2" border="0"></a>

</p>
<p>
Select the size of your VM and configure administrator account info by creating a username and password. Confirm licensing and hosting rights. Select "Next:Disk" to continue creating your VM. 
</p>
<br />

<p>
<a href="https://ibb.co/Sysydrn"><img src="https://i.ibb.co/h979ZfW/Untitled3.png" alt="Untitled3" border="0"></a>
</p>
<p>
Select "Next:Network" from the Disk page (no changes are neccessary on the Disk page). Select "create new" under Virtual Network and name your Virtual Network "Lab-VNet" for the purpose of this tutorial. Select "OK" and from this page you can select "Review + Create" to begin deploying your Windows VM. 
</p>
<br />

<br />

<p>
  

<a href="https://ibb.co/VjtXJWP"><img src="https://i.ibb.co/YR3vP7q/Untitled-4.png" alt="Untitled-4" border="0"> <a href="https://ibb.co/frmj6KV"><img src="https://i.ibb.co/gtskqXb/Untitled-5.png" alt="Untitled-5" border="0"></a>
</p>
<p>
Select "Create" and wait for the deployment to complete. Repeat the above steps to create your Linux VM; using the same Resource Group, size, and admin settings. Name your Linux VM "linux-vm" and select "Ubuntu Server 20.04 LTS - x64 Gen2" for your image.
</p>
<br />

<h2>Configuring NSGs: High-Level Steps</h2>

- Step 1 Delete An Inbound Security Rule for both VM1 and VM2. 
- Step 2 Add A New Inbound Security Rule for both VM1 and VM2. 


<h2>Actions and Observations</h2>

<p>
<a href="https://ibb.co/w0mgMYj"><img src="https://i.ibb.co/znvxGND/Untitled-6.png" alt="Untitled-6" border="0"></a>
</p>
<p>
In MS Azure navigate to Network Secruity Groups and select VM1 (windows-vm). Delete the first rule named "RDP".
</p>
<br />

<p>
<a href="https://ibb.co/qBQyHSn"><img src="https://i.ibb.co/R2wvXFS/Untitled-7.png" alt="Untitled-7" border="0"></a>
</p>
<p>
Select to add a new rule. Change the "destination port ranges" field to " * " (this represents "any"). Edit the name of this rule to "DANGER_AllowAnyCustomAnyInbound" and select "Add" to add this new rule. Repeat the same steps for VM2 (linux-vm). 
</p>
<br />
