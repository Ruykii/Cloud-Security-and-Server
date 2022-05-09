## Linux Admin and hardening Notes
Access Controls
	Grants permission to access documents and files on a host. 
		-Item can be a directory or a file. 
		-owner. Group, or other that are the groups for owners of the item. 
			-owner is the user who created the item (can be changed).
			-Group is the primary group associated with the creator. (can be changed)
			-Other is everyone who is not the owner and not in the group. 
It is called Discretionary Access Control (DAC), it is discretionary because item permissions can pass from one subject to another. 
Mode of the file is the rewrite attribute

| Command  | Function   |
|----------|------------|
| ls -l    | Shows the permissions info    | 
| chmod    | change the permissions info | 
| chown    | Change the owner and the group | 
| systemctl| To see service system -t service -all |
| systemctl status | Top see all status service |
| systemctl stop {nameofservice} | To stop the service |
| smbd.servce | run samba |
| systemctl disable | To stop the app |
| system crtl restart | To restart service |
| sudo apt remove | remove an app | 

## File permissions: 
![file permission](https://cdn.discordapp.com/attachments/792243138890694660/973286769317527592/unknown.png)

Servers are computers that offer services to other computers. 
	-A service is a function or capability that a machine makes available to another. 

Samba is a file sharing protocol, allows user to view and download and stores files remotely. 
Finding and stopping SMB Demo: If a malicious user is able to gain access to stop it you uninstall from the system. 
Service users are dedicated to running their own specific service. Typically, when you install a service with the package manager, a service user is automatically created and configured. Separation of duties can apply to nonentity accounts. Easy to start, stop, and manage the service. They are run by specific specific service user like crony. 
	-Hackers can hack them, do not allow people to log in and should only be interacted by servers. 
	-A service account usually has a system UID less than 1000 and cannot log in to use a shell. 
Chkrootkit and lynis for the homework, requires option and parameters 
