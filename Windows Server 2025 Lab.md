Windows Server 2025: Active Directory & RBAC Security Lab

## Optimized VM performance to run a modern 2025 server on legacy 2015 hardware

## Project Overview:
The goal of this lab was to simulate a real-world corporate IT environment by implementing Role-Based Access Control (RBAC) on a Windows Server 2025 instance. 
I successfully provisioned Active Directory objects, hardened file system security via NTFS permissions, and deployed a hidden network share to ensure data 
confidentiality.

## Tools Used:
Operating System: Windows Server 2025 (Standard Edition)

Hypervisor: VirtualBox (Running on a 2015 MacBook Pro)

Directory Services: Active Directory Domain Services (AD DS)

Network Protocol: SMB (Server Message Block) for hidden shares

## The Active Directory
In the GS_Accounting Properties, I implemented user1 as the type of name for the user group. To verify this object name by clicking on "Check Names", it shows
# User1: This is the specific Username assigned to the user.
# @: A seperator mostly used while sending email.
# NICOLENET.local: This is my Domain Name, the private network I built on the windows server.

<img width="2560" height="1600" alt="User1_image" src="https://github.com/user-attachments/assets/45576841-cf05-44d9-8562-fdfc81c0a2be" />
<img width="2560" height="1600" alt="User1 #2_image" src="https://github.com/user-attachments/assets/07c0b6db-8a6c-4389-8c6a-d822cea11792" />

## Hardening the File System (NTFS Permissions)
I made the Accounting department the only department to have access to sensitive data, by modifying the NTFS permissions for the C:\\Accounting_Data folder.
# Disabling Inheritence: I disabled the permission inheritence to break the connection between the parent drive to allow custom settings.
# Removing Default Access: Removing the standard "Users" group prevents other employees outside of the Accounting department from viewing the folder.
# Applying Principle of Least Priviledge: I added the GS_Accounting group and granted them Modify permissions. This allows authorized users to read, write, and delete files within the folder while preventing them from changing the folder's security settings themselves.

<img width="2560" height="1600" alt="adanved setting 2_image" src="https://github.com/user-attachments/assets/1381b38b-6af6-41bf-9c62-6f740391889e" />
<img width="2560" height="1600" alt="advanced setting 5_image" src="https://github.com/user-attachments/assets/093fd746-dd63-4fca-8ea4-cee8a8682bfa" />
<img width="2560" height="1600" alt="advanced setting 6_image" src="https://github.com/user-attachments/assets/f3f361d0-d97a-40a9-b546-6a0229b0996a" />

## The Test File
The final Security tab shows the hardened state: the "Users" group is completely gone, and GS_Accounting is listed with the correct permissions. To test this, I successfully created a test document called Financial Report 2026.txt inside the folder.

<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_15_02_2026_23_15_00" src="https://github.com/user-attachments/assets/8a640750-c369-40bf-b24c-d11ad4cf7507" />

## Network Sharing & Mapping
# The creation of the hidden share: After setting the permissions, I had to make the folder available over the network. I used an Administrative Hidden Share (Accounting$) so that the folder wouldn't be visible to anyone just browsing the network.
# Mapping the Drive to A: To make the folder easy for User1 to find, I mapped the network path to a dedicated A: Drive.
# Final Verification: It shows the user looking at their files through the mapped drive, proving that the permissions, the hidden share, and the mapping all work perfectly.

<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_15_02_2026_23_16_29" src="https://github.com/user-attachments/assets/9278ee02-d3ae-4220-bf93-063bea532bc1" />
<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_15_02_2026_23_22_06" src="https://github.com/user-attachments/assets/0e7403c7-533c-427a-aa40-3d432612592c" />
<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_15_02_2026_23_23_13" src="https://github.com/user-attachments/assets/801a40e8-f8d7-48cb-b4f7-c9411edc85a3" />
<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_16_02_2026_21_51_22" src="https://github.com/user-attachments/assets/f25a3042-ba70-4d5b-8d4a-465c2f00fbbb" />
<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_16_02_2026_21_52_00" src="https://github.com/user-attachments/assets/a68ebc34-7c52-4483-ad28-103be0ee6fa2" />
<img width="2560" height="1600" alt="VirtualBox_Window Server 2025_15_02_2026_22_49_00" src="https://github.com/user-attachments/assets/7502e3c1-4f0b-4c73-a5db-753e0e507d49" />
