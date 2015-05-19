
# Installation of a system on personal VirtualBox instance

Should investigate `vagrant` for controlling VirtualBox. Hints about `vagrant` can be found in the [unidata python workshop](https://github.com/duncombe/unidata-python-workshop/blob/master/VAGRANT_README.md) material (original [here](https://github.com/Unidata/unidata-python-workshop/blob/master/VAGRANT_README.md)).

## Installation Steps

For installation on VirtualBox instance: 

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
	   We want git >1.7.11; CentOS only installs 1.7.1 (or something).  Look at the last post [in this thread](http://serverfault.com/questions/448814/yum-doesnt-install-latest-version-of-git-on-centos6)
       ```
CentOS supports a "parallel" universe of newer compilers and tools, that doesn't clobber the older versions. You want

yum install devtoolset-2
Once it is installed, do

scl enable devtoolset-2 bash
which will modify your path. You'll have the old version of git in /usr/bin/git, and the newer version in /opt/rh/..../git. The newer one is 1.8.4/.

You also get newer g++ (4.8), etc.

      ```
  
     OR [try this                     page](http://tecadmin.net/install-git-1-9-on-centos-rhel/)
which gives the following:

      ```
# yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
# cd /usr/src
# wget https://www.kernel.org/pub/software/scm/git/git-1.9.4.tar.gz
# tar xzf git-1.9.4.tar.gz

# cd git-1.9.4
# make prefix=/usr/local/git all
# make prefix=/usr/local/git install
# echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/bashrc
# source /etc/bashrc

      ```
      
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

