<!--
See Part 2_Deploying Active Directory around minute (18:05)
-->

<p align="center">
<img src="https://github.com/user-attachments/assets/5f0f9ad2-0f1e-406e-8ff3-c5ce5e145a2b" alt="Microsoft Active Directory Logo"/>
</p>


# Chapter 5: Join a Windows 10 Pro Client to a Windows 2022 Server Domain Controller

1. Remote into the Windows 10 Pro Client
2. Change the name of the Windows 10 Pro virtual machine.
3. Join the Windows 10 Pro Client to the Windows 2022 Server Domain Controller.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)


<!--
<h2>High-Level Deployment and Configuration Steps</h2>
-->

<h2>High-Level Configuration Steps</h2>

- Part 1: [Remote into the Windows 10 Pro Client with Remote Desktop](https://github.com/ian-bates-it/Join-A-Client-To-A-Domain?tab=readme-ov-file#remote-into-the-windows-10-pro-client-with-remote-desktop)
- Part 2: [Join the Windows 10 Pro Client to the Windows 2022 Server Domain](https://github.com/ian-bates-it/Join-A-Client-To-A-Domain?tab=readme-ov-file#join-the-windows-10-pro-client-vm-to-our-windows-2022-server-domain)
- Part 3: [Confirm the Windows 10 Pro Client has joined the Domain in Active Directory Users and Computer Domain > Computers Directory](https://github.com/ian-bates-it/Join-A-Client-To-A-Domain?tab=readme-ov-file#confirm-that-the-windows-10-pro-client-has-joined-the-domain)



<h2>Prerequisites</h2>

1. Complete [Chapter 1 of this series, Creating a Windows 10 Pro and Windows 2022 Server Virtual Machines in Azure.](https://github.com/ian-bates-it/Azure-Virtual-Machine-Setup)

2. Complete [Chapter 2 of this series, Configuring the DNS settings for our Windows 10 Pro (Client) and Windows 2022 Server (Domain Controller).](https://github.com/ian-bates-it/Azure-Controller-Client-Configuration)

3. Complete [Chapter 3 of this series, Installing Active Directory on a Windows 2022 Server VM and promoting it to a Domain Controller.](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server)

4. Complete [Chapter 4 of this series, Create Organizational Units and Users in Active Directory.](https://github.com/ian-bates-it/Active-Directory-Users-And-Computers)



<br />
<br />


---

<h1>Part 1:</h1>

<h2>Remote into the Windows 10 Pro Client with Remote Desktop</h2>

- In the Azure Virtual Machine management, we can find the public IP address of our Windows 10 Pro virtual machine as shown below.
- In this example, the public IP address for my Windows 10 Pro client VM was `20.81.44.196` as shown below.

  <img src="https://github.com/user-attachments/assets/b5509b35-93f7-4e43-a43e-5fa6b3b7f1fc" height="80%" width="80%" />



---
<br />

- Run `mstsc.exe` to open Remote Desktop.

  <img src="https://github.com/user-attachments/assets/4771c754-edbd-4845-9e40-2b2e51d28535" height="40%" width="40%" />

---
<br />

- Enter the Windows 10 Pro virtual machine public IP address into the User name field.
- Use the [administrator account details that you created when setting up your Windows 10 Pro virtual machine in Azure](https://github.com/ian-bates-it/Azure-Virtual-Machine-Setup?tab=readme-ov-file#administrator-account).
- In this example, the administrator account I created for my Windows 10 Pro VM was `helpdesk`.
- Complete the remote logon process to the Windows 10 Pro virtual machine as shown below.

  <img src="https://github.com/user-attachments/assets/b0665b95-0116-4768-9a3d-c95f8f429acf" height="50%" width="50%" />


<br />
<br />

---

<h1>Part 2:</h1>

<h2>Join the Windows 10 Pro Client VM To Our Windows 2022 Server Domain</h2>


<h3>Rename the Windows 10 Pro Client</h3>

- Click the Start Charm.
- Select `System`.
- Navigate to `About`.
- Click the link `Rename this PC (Advanced)` as shown below.

  <img src="https://github.com/user-attachments/assets/13c2f031-c6e6-45d2-ba5f-f2518f760410" height="80%" width="80%" />


---
<br />

<h3>Click `Change` in System Properties</h3>

- In the `System Properties` window, under the `Computer Name` tab, click the `Change` button as shown below.


  <img src="https://github.com/user-attachments/assets/64a40877-1903-4ca4-bbab-ea5337160874" height="60%" width="60%" />


---
<br />

<h3>Change Member Of from Workgroup to Domain</h3>


1. Change the default `Computer Name`. Here I changed it to `helpdesk`.
2. Click **Domain** and enter the [domain name we created when promoting our Windows 2022 Server to a Domain Controller](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server?tab=readme-ov-file#deployment-configuration).
3. Click `OK` to continue as shown below.



  <img src="https://github.com/user-attachments/assets/7fd00c9e-bb89-4045-a66f-4396d47712f8" height="80%" width="80%" />



---
<br />

<h3>Approve Change With Admin User</h3>

- Use the administrative user account we created [when we added an admin user in Active Directory Users and Groups at this link](https://github.com/ian-bates-it/Active-Directory-Users-And-Computers?tab=readme-ov-file#create-a-new-user-in-active-directory).
- In my example, the admin user account I created was `Jane Doe` with username `jdoe`.

To approve the Domain Changes, do the following.
1. Specify the context by adding the Domain Controller domain name as a prefix to the admin username. In this example that would be `IanBates.com` followed by `\jdoe`
2. Enter the admin user password.
3. Click `OK` as shown below.


  <img src="https://github.com/user-attachments/assets/e5fff840-632f-4633-bf96-6588a5ebbea5" height="60%" width="60%" />



---
<br />

<h3>Restart the Windows 10 Pro Client</h3>

- You should get confirmation that you have joined the Windows 10 Pro to the domain, with a welcome message like the one shown below.

  <img src="https://github.com/user-attachments/assets/51d0b46e-d478-4ba4-8190-0ee47a54c5aa" height="40%" width="40%" />


- You will then be prompted to restart the Windows 10 Pro virtual machine.
- Follow the prompts to do so.

  <img src="https://github.com/user-attachments/assets/6602695f-126c-4abf-b3d6-3c38bae62d9e" height="40%" width="40%" />



<br />
<br />

---

<h1>Part 3:</h1>

<h3>Confirm that the Windows 10 Pro Client Has Joined The Domain</h3>


- Remote into the Windows 2022 Server Controller virtual machine.
- Open `Active Directory Users and Computers`

1. Click on the Domain. Here that would be `IanBates.com`
2. Click on `Computers`. The Windows 10 Pro virtual machine should be listed. Here, my Windows 10 Pro virtual machine named `HELPDESK` has successfully joined our domain as shown below.

  <img src="https://github.com/user-attachments/assets/33984379-ea69-4e3f-8ef8-e2cbdc62f8c7" height="80%" width="80%" />



