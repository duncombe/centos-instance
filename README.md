Installation of Minimal CentOS-6.5
==================================

Installation Steps
------------------

1.  Edit network-scripts to get networking up

vi /etc/sysconfig/network-scripts/eth0

ONBOOT=yes

NM\_CONTROLLED=no

2.  yum install man
3.  yum install git
4.  yum install python

This provides python 2.6.6. We need 2.7.6.

5.  useradd duncombe
6.  yum -y update
7.  test if pip works
8.  STOP! Restart!

1.  Start a VM, install minimal CentOS.
2.  Add a user

adduser duncombe

passwd duncombe

visudo

3.  Edit network-scripts.

vi /etc/sysconfig/network-scripts/ifcfg-eth0

ONBOOT=yes

NM\_CONTROLLED=no

service network restart

\# edit for broken DHCP server

\# edit /etc/sysconfig/network-scripts/ifcfg-eth0

        \# edit /etc/sysconfig/network

        \# edit /etc/resolv.conf

4.  yum -y update
5.  yum install wget
6.  yum install man
7.  yum install git
8.  yum install vim
9.  yum install ntp
10. bash Anaconda...sh
11. git clone compliance-checker
12. git clone virtualenv-burrito
13. Does not run. Email matt ASAP.

Does not have, and may need
---------------------------

-   Minimal version of vim installed, upgrade to more full-featured vim.


