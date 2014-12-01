
# Using AWS Instance Provided

Provides some notes on installing, accessing and using the NODC Amazon Web Service VM. 

Please pay attention to this next point. At some places below is mentioned to clone a repository from github.com/duncombe:
- READ AND UNDERSTAND CAREFULLY ALL SOFTWARE BEFORE YOU INSTALL AND RUN IT.    
  What works for me MAY NOT work for you. I use a lot of custom scripts, functions and aliases that suit my programming style and workflow. These may not work for you and may break the setup you are trying to create. Hints from the name about what a software does may not be 100% accurate. Some functions and scripts may have unexpected side effects. 

###Housekeeping    
	Downloads live in ~/software.    

### For AWS instance provided: 

More hints and tips are available in the document on [running a personal VM on Oracle VirtualBox](personal-vbox-install.md).

2. User provides sysadmin with public key and keeps private key and passphrase.
1. Sysadmin provides IP of instance. 
2. Putty in to instance with key and passphrase. Set putty to send keep-alive pings.
2. We do need   
	* `ssh-keygen` \# then put the key on github
	* `git clone duncombe/dotfiles`  \# and adjust the bashrc, and other dotfiles   
2.  We do not need these steps from the personal install:   
  	- `yum -y update`  \# we don't get to do this, no sudo access
	- `yum install wget`  \# already installed
	- `yum install man`   # already installed
	- `yum install git`   # already installed  (v. 1.7.1, need > 1.7.11. Also see [the document for running on Oracle VirtualBox](personal-vbox-install.md).)
	- `yum install vim`   # already installed (v. 7.2)
	- `yum install ntp`   # already installed but stopped. Now started by sysadmin, thanks!
3.  May need to have sysadmin enable access to `cron`, `at` and `batch`, which currently are not permitted to run. Not right now a huge issue, but you may need these when the time comes to test databases and servers.
4. See [http://docs.continuum.io/anaconda/install.html](http://docs.continuum.io/anaconda/install.html) for installation 
	of anaconda:
	1.	Get the anaconda install script    
		`wget  http://09c8d0b2229f813c1b93-c95ac804525aac4b6dba79b00b39d1d3.r79.cf1.rackcdn.com/Anaconda-2.1.0-Linux-x86_64.sh`    
	then   
		- `bash Anaconda...sh`    
		- answer the questions and anaconda
	installs into `~/anaconda` directory.    
	Can choose to have it change your path or you will have to change it yourself by prepending `PATH=~/anaconda/bin` 
	to PATH in one of `.bashrc` or `.bashrc_custom`, wherever is appropriate.     
		- Already have anaconda installed and want to upgrade to latest version?      
		```
		conda update conda    
		conda update anaconda    
		```       
5. See [here](python_setup.md) for setting up the python environment.    
    
5. Get Hugo (for sos-guidelines documentation).     
		- download from github     
		`wget https://github.com/spf13/hugo/releases/download/v0.12/hugo_0.12_linux_amd64.tar.gz`
6. `git clone compliance-checker`  
7. Set up an environment. The IOOS site recommends    
	i. `git clone virtualenv-burrito`   
	ii.  but compliance-checker does not run. What now?    
	iii.  Well, NOW we use anaconda and follow some instructions in  the Unidata python workshop examples. Also have a 		look at Rich Signell's
	[tiddly spot blog](http://rsignell.tiddlyspot.com/#[[Creating%20a%20custom%20Conda%20environment%20on%20Wakari%20Enterprise]])
	for hints.     
13. Further exciting python information is in this repository at [python_setup.md](python_setup.md).

