<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Enforcing Group Policy and Account Management within Active Directory (Azure VMs)</h1>
This overview outlines the application of group policy and account management within Active Directory.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2025
- Windows 10 (21H2)

<h2>High-Level Use Cases and Configuration Steps</h2>

- Enabling Remote Desktop Across Many Domain-Joined Systems
- Dealing with Account Lockouts and Configuring Settings
- Enabling and Disabling Accounts
- Observing Machine Logs

<h2>Use Cases and Configuration Steps</h2>

<p>
<img width="2636" height="1402" alt="image" src="https://github.com/user-attachments/assets/a41fb08d-23ec-455b-8423-abfd2ff511a7" />
</p>
<p>
To enable RDP access across multiple domain-joined systems, start by navigating to Active Directory Users and Computers, creating a Global Security Group, and adding all users who should have RDP access. Open Group Policy Management (Run > gpmc.msc), right-click the OU that contains computer accounts and select Create a GPO in this domain and link it here. Edit the GPO by going from Computer Config, Policies, Admin Templates, Windows Components, Remote Desktop Services, Session Host, and Connections. Enable users to connect remotely using RDS. Go back to Preferences, Control Panel Settings, and local users and groups to add a new group and the members from the Global Security Group previously made to avoid breaking existing access. Allow log on through Remote Desktop Services for the new group by going from Policies, Windows Settings, Security Settings, Local Policies, and User Rights Assignment. Verify they are not denied in the deny log on through Remote Desktop Services. Finally, enable the Windows Firewall Rule for RDP with a predefined 'Remote Desktop- User Mode (TCP-In) rule.   
</p>
<br />

<p>
<img width="2880" height="1702" alt="image" src="https://github.com/user-attachments/assets/9eb36edb-2e81-4f3e-94f0-7061498c1669" />
</p>
<p>
To configure account lockout settings, start by opening the Group Policy Management Console. Edit the default domain policy (or create a new GPO) and navigate to the Account Lockout Policy Settings (Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy). There will be three primary settings to configure: Lockout Duration, Lockout Threshold, Allow Administrator Account Lockout, and Reset Account Lockout After. Once settings are configured, apply the GPO to an OU. The policy will update automatically or can be forced via PowerShell using gpupdate /force. To reset user's password, search for the user within ADUC, right-click their name, and select reset password. This will give you the option to enter a new password and/or check the 'unlock the user's account' box.
</p>
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
