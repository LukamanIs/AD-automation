Active Directory Automation & User Management
PowerShell-based automation lab for managing user accounts and enforcing security policies in a Windows Server Active Directory environment.

🔧 Project Overview
This project demonstrates the setup and management of a Windows Server 2022 domain controller along with Active Directory tasks automated using PowerShell. The environment simulates real-world help desk and system administration duties, such as account provisioning, password resets, and group policy enforcement.

⚙️ Technologies Used
Windows Server 2022 (VirtualBox or Hyper-V)

Active Directory Domain Services

PowerShell

Group Policy Management Console (GPMC)

Windows 11 Client (Domain Joined)

🚀 Key Features
✅ Domain Controller installation and configuration

✅ Created and managed Organizational Units (OUs)

✅ Automated new user creation and password resets using PowerShell

✅ Applied Group Policy Objects (GPOs) for:

Password complexity

Account lockout policies

Login restrictions

✅ Connected Windows 11 VM to the domain for testing

📂 PowerShell Scripts
powershell
Copy
Edit
# Add new user with default password
New-ADUser -Name "John Doe" -GivenName "John" -Surname "Doe" -SamAccountName "jdoe" `
-UserPrincipalName "jdoe@domain.local" -AccountPassword (ConvertTo-SecureString "Temp123!" -AsPlainText -Force) `
-Enabled $true -Path "OU=Staff,DC=domain,DC=local"

# Reset password
Set-ADAccountPassword -Identity "jdoe" -NewPassword (ConvertTo-SecureString "SecurePass456!" -AsPlainText -Force)

# Force password change at next logon
Set-ADUser -Identity "jdoe" -ChangePasswordAtLogon $true
