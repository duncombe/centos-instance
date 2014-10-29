

For AWS instance provided:

1.  Putty in with key and passphrase. Set putty to send keep-alive pings.
2.  We do need   
	* `ssh-keygen` \# then put the key on github   
	* `git clone dotfiles`  \# and adjust the bashrc, and other dotfiles   

	
2.  We do not need:   
  	- `yum -y update`  \# we don't get to do this, no privilege
	- `yum install wget`  \# already installed
	- `yum install man`   # already installed
	- `yum install git`   # already installed  (v. 1.7.1, need >1.7.11. See also above comments for VBox.)
	- `yum install vim`   # already installed (v. 7.2)
	- `yum install ntp`   # already installed but stopped
4. Get the anaconda install script    
	`wget  http://09c8d0b2229f813c1b93-c95ac804525aac4b6dba79b00b39d1d3.r79.cf1.rackcdn.com/Anaconda-2.1.0-Linux-x86_64.sh`    
	then
	- `bash Anaconda...sh`   

5. Get Hugo (for sos-guidelines documentation).
	- download from github    
	`wget https://github.com/spf13/hugo/releases/download/v0.12/hugo_0.12_linux_amd64.tar.gz`


11. `git clone compliance-checker`  
12. `git clone virtualenv-burrito`  
13.  compliance-checker does not run. What now?