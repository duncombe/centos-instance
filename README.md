Installation of Minimal CentOS-6.5
==================================

Installation Steps
------------------

1.  Start a VM, install minimal CentOS.

    Using VirtualBox, Centos-6.5 minimal iso.  

2.  Add a user

   `adduser $USER`  
   `passwd $USER`  
   `visudo`  # so that we don't have to remember a root password, only user.


3.  Edit network-scripts.
   - `vi /etc/sysconfig/network-scripts/ifcfg-eth0`  
   	> `ONBOOT=yes`  
   	> `NM_CONTROLLED=no`  
   - \# edit for broken DHCP server  
		\# `edit /etc/sysconfig/network-scripts/ifcfg-eth0`  
		\# `edit /etc/sysconfig/network`    
		\# `edit /etc/resolv.conf`    
	`service network restart`
   - For VirtualBox, remember to connect/activate the appropriate network connection (wlan0 or eth0).
  
4.  Once networking is up,
	- `yum -y update` 
	- `yum install wget`  
	- `yum install man`  
	- `yum install git`  
	- `yum install vim`  
	- `yum install ntp`   
   		`service ntpd start`  

10. Get the anaconda install script, where? then
	- `bash Anaconda...sh`  

11. `git clone compliance-checker`  
12. `git clone virtualenv-burrito`  
13.  compliance-checker does not run. What now?


## Failed Attempts

1.  Edit network-scripts to get networking up
  
  `vi /etc/sysconfig/network-scripts/eth0`  
     `ONBOOT=yes`  
     `NM_CONTROLLED=no`  

2.  `yum install man`
3.  `yum install git`
4.  `yum install python` 
   This provides python 2.6.6. We need 2.7.6.  

5.  `useradd $USER`
6.  `yum -y update`
7.  test if pip works
8.  STOP! Restart!


Trying again:


