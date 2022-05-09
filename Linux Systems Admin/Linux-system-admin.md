## Ensure Permissions on Sensitive Files
Step 1: Ensure/Double Check Permissions on Sensitive Files


Permissions on /etc/shadow should allow only root read and write access.


Command to inspect permissions: ls -l /etc/shadow


Command to set permissions (if needed): chmod owner:root /etc/shadow




Permissions on /etc/gshadow should allow only root read and write access.


Command to inspect permissions:ls -l /etc/gshadow


Command to set permissions (if needed):sudo chmod owner:root /etc/gshadow




Permissions on /etc/group should allow root read and write access, and allow everyone else read access only.


Command to inspect permissions: ls -l /etc/group


Command to set permissions (if needed):sudo chmod owner:root /etc/group




Permissions on /etc/passwd should allow root read and write access, and allow everyone else read access only.


Command to inspect permissions:ls -l /etc/passwd


Command to set permissions (if needed):sudo chmod owner:root /etc/passwd





## Step 2: Create User Accounts


Add user accounts for sam, joe, amy, sara, and admin.

Command to add each user account (include all five users):
Sudo adduser 


Ensure that only the admin has general sudo access.

Command to add admin to the sudo group:
Sudo usermod -aG sudo admin



## Step 3: Create User Group and Collaborative Folder
Adding group `engineers' (GID 1019) 
Sudo addgroup engineers



Add an engineers group to the system.

Command to add group:



Add users sam, joe, amy, and sara to the managed group.

Command to add users to engineers group (include all four users):
Sudo usermod -aG engineers sam 
Sudo usermod -aG engineers joe
Sudo usermod -aG engineers sara
Sudo usermod -aG engineers amy


Create a shared folder for this group at /home/engineers.


Command to create the shared folder:
Sudo mkdir -p /home/engineers


Change ownership on the new engineers' shared folder to the engineers group.

Command to change ownership of engineer's shared folder to engineer group:

Sudo chgrp -c[v I needed to see if it worked] engineers /home/engineers 


## Step 4: Lynis Auditing


Command to install Lynis:
Sudo apt install Lynis

Command to see documentation and instructions:
Sudo lynis show commands

Command to run an audit:
Sudo lynis audit system 

![Lynis output that hardens the system](https://cdn.discordapp.com/attachments/792243138890694660/973283575568928788/unknown.png)
![another image](https://cdn.discordapp.com/attachments/792243138890694660/973283648587579492/unknown.png)
![another](https://cdn.discordapp.com/attachments/792243138890694660/973283702740234301/unknown.png)
