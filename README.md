# Building An Active Directory Home Lab
---

<img width="720" height="344" alt="Image" src="https://github.com/user-attachments/assets/5d028067-a0a6-4d5b-831f-d949bb4230f8" />


---

# Introduction

**Active Directory (AD) is the backbone of user and access management in most Windows enterprise networks. This project demonstrates how to build a simple Active Directory home lab from scratch for hands-on learning and practice.**

# What is Active Directory?

**Active Directory is Microsoft’s centralized system for managing users, computers, and permissions within a Windows domain. It handles authentication and access control, making it essential in enterprise environments.**

# What is a Domain Controller?
**A Domain Controller (DC) is the central and most critical component in an Active Directory environment. It stores the directory (our phonebook) and handles authentication, authorization, and administrative tasks such as managing user accounts, applying group policies and enforcing security settings. Essentially, it is the brain behind the AD environment.**

# Why this Project?
If you’ve ever wanted to build your own Active Directory lab but weren’t sure where to begin, you’re in the right place. In this article, I’ll guide you step-by-step through setting up an AD lab environment that’s perfect for learning, testing, or practicing cybersecurity skills.

# Lab Requirements
**Set up the following virtual machines using VMware Workstation:**

**1 x Windows Server 2022 (Domain controller) 2 x Windows 10 Enterprise — User-machine 1 and 2 Minimum System Requirements:
RAM — Minimum 16GB
Disk Space — Minimum 60GB
Downloading Required ISOs
Download the required ISOs from the official Microsoft Evaluation Center using the links below:**

Windows 10 ISO
Windows Server 2022 ISO
<img width="1400" height="543" alt="Image" src="https://github.com/user-attachments/assets/81fdd69b-5d5f-4c2e-b026-06f02be3871a" />

<img width="720" height="315" alt="Image" src="https://github.com/user-attachments/assets/c3157602-fa7d-4a7b-8ab4-32bf64393724" />

Simply complete the trial registration form to access the download. You don’t need to use a real name or email. Just fill it out and click Download.

<img width="720" height="322" alt="Image" src="https://github.com/user-attachments/assets/67855426-26bc-4f31-b50c-400cfbecd536" />

<img width="1400" height="682" alt="Image" src="https://github.com/user-attachments/assets/020ba4d1-93c6-46a3-81d7-85f18867d266" />

Ensure you download the 64-bit edition.

<img width="1400" height="671" alt="Image" src="https://github.com/user-attachments/assets/362c0351-59d2-463e-821a-beebe94b8d51" />

<img width="1400" height="641" alt="Image" src="https://github.com/user-attachments/assets/e841c4e8-92b1-401f-90b3-fde8b87d4b94" />
---

# Setting up the Domain Controller

Once you’ve downloaded the required files, we’ll move on to configuring  **Windows Server 2022** in VMware to set up the **domain controller.**

Start by creating a new virtual machine, then select the ISO file.

<img width="1400" height="516" alt="Image" src="https://github.com/user-attachments/assets/d53951d9-2a32-4b71-8e35-e22336b805f0" />

<img width="640" height="634" alt="Image" src="https://github.com/user-attachments/assets/ff5e1f15-fb8c-48e5-8b83-b2088763e0eb" />

Select the Windows Server 2022 **ISO file**, then click **Next.**
<img width="636" height="636" alt="Image" src="https://github.com/user-attachments/assets/c36e96d0-8391-4061-8f2a-6af41911f469" />

Select the operating system and version. The highest server version in the list is Windows Server 2016, which is fine.


<img width="640" height="631" alt="Image" src="https://github.com/user-attachments/assets/9172d8bc-4b10-480f-916f-ed9634ede3a3" />

Choose a storage location for the virtual machine, then click Next.

Make sure to select a drive with at least 60 GB of free space to store your files.


Before powering on the machine, let’s adjust the virtual machine settings.
Press enter or click to view image in full size

Allocate sufficient memory based on your system’s capacity. For this demonstration, I’m using 4 GB of RAM. Also, ensure the network setting is configured to NAT.
Press enter or click to view image in full size

Now power on virtual machine and quickly press any key to begin the installation.
Press enter or click to view image in full size

Follow the on-screen prompts to complete the installation.
Press enter or click to view image in full size

Press enter or click to view image in full size

Select Windows Server 2022 Standard Evaluation (Desktop Experience) from the list.
Press enter or click to view image in full size

Press enter or click to view image in full size

Click on Custom: Install.
Press enter or click to view image in full size

Create a new drive by clicking New, then apply the changes to proceed.
Press enter or click to view image in full size

Press enter or click to view image in full size

Press enter or click to view image in full size

The installation may take some time, so be patient.
Press enter or click to view image in full size

Allow the machine to reboot automatically. This may take a few minutes to complete the installation.
Press enter or click to view image in full size

You’ll now be prompted to create a password for the Administrator account. For this demonstration, I’m using a weak password.
Press enter or click to view image in full size

Use the Send Ctrl + Alt + Del option to unlock the screen.
Press enter or click to view image in full size

Enter the password to log in.
Press enter or click to view image in full size

Once logged in, the first step is to rename the computer.
Press enter or click to view image in full size

Click on Rename this PC and enter your preferred name, such as HYDRA-DC.

Press enter or click to view image in full size

Proceed to restart the machine.
Press enter or click to view image in full size

Log back in. Now, to set up this system as a domain controller, start by adding Roles and Features. Click Next until you reach the Server Roles step.
Press enter or click to view image in full size

Check Active Directory Domain Services and click Add Features. Then continue clicking Next to proceed.
Press enter or click to view image in full size

Check the option Restart the destination server automatically if required, then click Install.
Press enter or click to view image in full size

Press enter or click to view image in full size

The installation will take a few minutes to complete and set up the domain controller.
Press enter or click to view image in full size

After the installation completes, proceed to promote the server to a domain controller.
Press enter or click to view image in full size

Create a new forest and enter a domain name of your choice. Once done, click Next.
Press enter or click to view image in full size

Set and confirm a password for Directory Services Restore Mode, then continue clicking Next until you reach the Prerequisites Check section.
Press enter or click to view image in full size

Wait for the prerequisite check to complete, then click Install to proceed.
Press enter or click to view image in full size

Press enter or click to view image in full size

The installation will begin and prompt a reboot once finished. Click Close and the system will restart automatically and return to the login screen.
Press enter or click to view image in full size

Press enter or click to view image in full size

We can now see that the login is being performed as MARVEL\Administrator.
Press enter or click to view image in full size

Next, we need to set up Active Directory Certificate Services (AD CS), which will allow us to perform certain attacks later. Open Add Roles and Features again and click Next to continue.
Press enter or click to view image in full size

Select Active Directory Certificate Services. In simple terms, Certificate Services are used to validate identities within a domain environment.
Press enter or click to view image in full size

Keep clicking Next to proceed through the setup.
Press enter or click to view image in full size

Press enter or click to view image in full size

Ensure that Certification Authority is selected before continuing.
Press enter or click to view image in full size

Select Restart destination server automatically if required, then click Install to begin the setup.
Press enter or click to view image in full size

Once the installation is complete, proceed to configure AD CS on the destination server.
Press enter or click to view image in full size

Press enter or click to view image in full size

Ensure that Certification Authority is checked, then continue clicking Next to move through the configuration steps.
Press enter or click to view image in full size

On the Cryptography settings page, leaving SHA256 as the default is perfectly fine.
Press enter or click to view image in full size

Press enter or click to view image in full size

For the validity period, set it to 99 years in case you plan to keep this lab environment running long term.
Press enter or click to view image in full size

Press enter or click to view image in full size

That’s it for this section. Go ahead and reboot your server so we can move on to setting up the user machines.
Press enter or click to view image in full size

Press enter or click to view image in full size

Setting up the User Machines
Now that the domain controller is set up, it’s time to move on to the user machines. To conserve RAM, go ahead and shut down the domain controller for now.
We’ll be building two user machines in this next step.

Press enter or click to view image in full size


Go ahead and select the Windows ISO, then click Next to continue.

Skip the product key step, and make sure to select Windows 10 Enterprise as the version.


Give your virtual machine a name, feel free to use any name you prefer.



Next, we’ll edit the virtual machine settings and remove the floppy disk from the hardware configuration.
Press enter or click to view image in full size


You can leave the memory at 2GB, and make sure the Network Adapter is set to NAT. Once that’s done, go ahead and power on the machine.
Press enter or click to view image in full size

Press enter or click to view image in full size

Press enter or click to view image in full size

Follow the installation prompts just like you did for Windows Server 2022. This part should be quicker, as it’s mostly a repetition of earlier steps. Let the machine reboot automatically when prompted.
Press enter or click to view image in full size

Press enter or click to view image in full size

When prompted, go ahead and skip the keyboard layout selection.
Press enter or click to view image in full size

At this point, you’ll see a screen asking if you want to sign in with a Microsoft account. Select Domain join instead.
Press enter or click to view image in full size

This option allows you to create a local account instead of signing in with a Microsoft account. Feel free to use any name of your choice for the username.
Press enter or click to view image in full size

Set a password and confirm it. For this lab, I’m using a weak password just to keep things simple.
Password1
Press enter or click to view image in full size

For the security questions, feel free to select any options and provide answers of your choice.
Press enter or click to view image in full size

Next, we’ll disable location services and turn off other optional settings to minimize data sharing.
Press enter or click to view image in full size

Press enter or click to view image in full size

Great, now that you’re logged in, go ahead and rename the PC to something meaningful for your lab setup.
Press enter or click to view image in full size

Press enter or click to view image in full size

Go ahead and restart the machine, then repeat the same setup process for the second user machine.

Second User Machine

Machine Name: SPIDERMAN
username:     peterparker
password:     Password1
Setting up Users, Groups and Policies
Next, we’ll modify the domain controller by setting up user groups and applying some policies. But first, let’s go ahead and power on the domain controller.

Press enter or click to view image in full size

Press enter or click to view image in full size

Right-click the domain name and select the option to create a new Organizational Unit (OU).
Press enter or click to view image in full size

Give the Organizational Unit a name of your choice, then click OK to create it.

Press enter or click to view image in full size

Select all the users in the Users folder, excluding the Administrator and Guest accounts — then drag and drop them into the Groups folder (the Organizational Unit we just created).
Press enter or click to view image in full size

Press enter or click to view image in full size

Now let’s create a few more accounts. First, we’ll create a Domain Admin account by duplicating the existing Administrator’s privileges. Right-click on the Administrator account, select Copy, and follow the prompts to set up the new account.
Press enter or click to view image in full size


Set a password of your choice and make sure it’s something you’ll remember, then hit Next. I’m using a weak password here to keep things simple.
Password12345!


The domain admin has now been successfully added.
Press enter or click to view image in full size

Next, let’s duplicate the Administrator account again to create a service account with domain admin privileges. Service accounts are typically used to run specific services, so in this case, we’ll create a SQL service account to manage a SQL Server instance.

Once again, set a password you’ll remember.
MYpassword123#

We can now see that the service account has been successfully created.
Press enter or click to view image in full size

Now double-click on it and add a note in the description field. We’re simulating what many domain admins do — assuming they’re the only ones who can see the password. In reality, any valid user can view the description.
The password is MYpassword123#

At this stage, let’s go ahead and create two standard users who will be part of the Domain Users group. To begin, right-click on an empty space in the user pane.
Press enter or click to view image in full size

Now, follow the prompts to complete the creation of both user accounts.
#First User
Frank Castle
fcastle
Password1

#Second User
Peter Parker
pparker
Password2
All our accounts are now set up just the way we want them.
Press enter or click to view image in full size

Let’s go ahead and create a file share that could potentially be exploited in future attack simulations.
Press enter or click to view image in full size

Click on Shares in the left-hand pane to begin setting up a new shared folder.
Press enter or click to view image in full size

Press enter or click to view image in full size

Keep clicking Next to proceed through the setup wizard.
Press enter or click to view image in full size

Go ahead and enter a name for the share, this will be the name users see when accessing the shared folder.
Press enter or click to view image in full size

Press enter or click to view image in full size

Keep clicking Next through the remaining prompts, then click Create to finish setting up the file share.
Press enter or click to view image in full size

Press enter or click to view image in full size

Next, we’re going to complete the SQL Service setup using the command prompt with administrative privileges.
Press enter or click to view image in full size

Run the below command, making sure to replace it with the actual name of your domain controller.
setspn -a HYDRA-DC/SQLService.MARVEL.local:60111 MARVEL\SQLService
Press enter or click to view image in full size

Confirm that the Service Principal Name (SPN) was successfully found.
setspn -T MARVEL.local -Q */*
Press enter or click to view image in full size

Now we’re going to set up a Group Policy.
Press enter or click to view image in full size

Next, let’s add a new policy. We’ll be creating a Group Policy that applies across the entire domain.
Press enter or click to view image in full size

Go ahead and give the policy a descriptive name so it’s easy to identify later.
Press enter or click to view image in full size

Now, let’s edit the newly created policy by right-clicking on it and selecting Edit.
Press enter or click to view image in full size

Press enter or click to view image in full size

Now we’re going to disable Windows Defender in our lab environment. This will allow us to execute various attack techniques freely. Please note that this lab setup does not cover antivirus evasion techniques.
Press enter or click to view image in full size

Scroll down to find Microsoft Defender Antivirus, then double-click it and set it to Enabled to turn it off.
Press enter or click to view image in full size

Press enter or click to view image in full size

Now we need to enforce the policy we just created. This ensures that any user or machine that joins the domain will automatically have Windows Defender disabled in accordance with the policy.
Press enter or click to view image in full size

Press enter or click to view image in full size

The final step is to configure a static IP address for the domain controller. Start by opening command prompt and checking the current IP configuration of the machine.
Press enter or click to view image in full size

Next, click on Network & Internet Settings from the taskbar.

Press enter or click to view image in full size

Press enter or click to view image in full size

Double-click on IPv4 and update the IP address, subnet mask, and default gateway based on your preferred network configuration. You can choose any values that suit your setup.


Next, we’ll proceed to join the user machines to our domain controller.

Joining our Machines to the Domain Controller
At this stage, we’re going to join both user machines to the domain controller. Ensure all machines are powered on before proceeding.

Become a member
First, we need to configure the DNS settings on both user machines by pointing them to the domain controller’s IP address. Make sure to apply this change on both systems.

Press enter or click to view image in full size

Next, we’ll connect the machines to the domain. Search for Domain in the Start menu and select Access work or school from the results.
Press enter or click to view image in full size

Press enter or click to view image in full size


Type in the domain name and click Next.

Now sign in using the Administrator credentials and click OK.



Next, go to the second machine and repeat the same steps. Once done, log back into the domain controller to verify that both machines have successfully joined the domain.
Press enter or click to view image in full size

Under the Computers section, we can now see that both machines have been successfully added to the domain.
Press enter or click to view image in full size

Now let’s switch back to the THEPUNISHER machine and log in as the administrator — we’ve got a few quick configurations to take care of.
Press enter or click to view image in full size

Click on Manage Local Users and Groups.
Press enter or click to view image in full size

Under Users, set a password for the local Administrator account.
Press enter or click to view image in full size

I added this password.
Password1!
Press enter or click to view image in full size

Now, double-click on the Administrator account, uncheck Account is disabled, and click OK.

The account is now enabled. While best practice recommends keeping it disabled, in many real-world environments you’ll often find local Administrator accounts left enabled. In the Groups section, we need to add one more user, Fcastle to the Administrators group.
Press enter or click to view image in full size


Type in the username, click Check Names to validate it, then click OK to confirm.


Now let’s ensure that Network Discovery is enabled on this machine.
Press enter or click to view image in full size

Click on Network, and you’ll notice that Network Discovery is currently turned off.
Press enter or click to view image in full size

Press enter or click to view image in full size

Network Discovery is now successfully turned on.
Press enter or click to view image in full size

Now move on to the second machine and repeat the same steps. This time, we’ll be adding two users pparker and fcastle to the local administrators group.

Also, make sure to turn on Network Discovery. Once that’s done, sign out of the SPIDERMAN machine and log back in as the local Administrator.
Press enter or click to view image in full size

Next, we’re going to set up a shared drive.
Press enter or click to view image in full size

Click on This PC, then select Map network drive from the top menu.
Press enter or click to view image in full size


Enter the Administrator credentials when prompted to authenticate the connection.

Now the shared drive has been successfully mapped and is accessible from this machine.
Press enter or click to view image in full size

Conclusion
And that’s it! We’ve successfully built an Active Directory home lab from scratch. But this is just the beginning. In the next blog post, we’ll dive into key attack scenarios such as LLMNR Poisoning, SMB Relay, MITM6 attacks, and more as we continue our AD lab walkthrough.

Keep in mind, practice is key. Building your own AD lab is a great way to sharpen your IT skills, get comfortable with AD environments, and gear up for real-world scenarios. Until the next blog post, keep learning, testing, and pushing your boundaries in the dynamic world of Active Directory.

Thanks for reading and Happy Hacking!

Active Directory
Domain Controller
Lab Setup
Homelab
6


1





