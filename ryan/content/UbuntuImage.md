# Ubuntu Images at DETER

Our Ubuntu images have full apt support for installing packages. The packages are mirrored locally on our package mirror [wiki:scratch].

## Ubuntu1404-64-STD

Ubuntu 14.04 LTS, 64 bit only.  32 bit version for bpc2800 nodes available as Ubuntu1404-32-STD. Full package mirror on scratch.

## Ubuntu1204-64-STD

Ubuntu 12.04 LTS, 64 bit only.  Full package mirror on scratch.

## Ubuntu1004-STD

Ubuntu 10.04 LTS.  Full package mirror on scratch.


### Updating custom Ubuntu1004-STD images to fix control network discovery race condition

Currently, we do not have an elegant method to automatically update client scripts on custom Ubutnu images.  This issue is important enough that you will want to update any Ubuntu images created before March 2, 2012.  Two files need to be updated, dhclient-exit-hooks and findcnet.  You should be able to copy and paste the commands below to easily update your image running on a testbed node.  After that simply take a snapshot to update your image.

	
	sudo curl --output /etc/dhcp3/dhclient-exit-hooks boss.isi.deterlab.net/downloads/client-update/Ubuntu1004-dhclient-exit-hooks
	sudo curl --output /usr/local/etc/emulab/findcnet boss.isi.deterlab.net/downloads/client-update/Ubuntu1004-findcnet
	sudo chmod a+rx /etc/dhcp3/dhclient-exit-hooks /usr/local/etc/emulab/findcnet
	sudo chown root:root /etc/dhcp3/dhclient-exit-hooks /usr/local/etc/emulab/findcnet
	

For example, I have my custom image loaded on pc031.

	
	[jhickey@users ~]$ ssh pc031
	Linux centos.jjh-centos.detertest.isi.deterlab.net 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
	Ubuntu 10.04.4 LTS
	
	Welcome to Ubuntu!
	 * Documentation:  https://help.ubuntu.com/
	
	  System information as of Mon Mar 12 16:00:28 PDT 2012
	
	  System load:  0.12              Processes:           135
	  Usage of /:   7.7% of 14.67GB   Users logged in:     0
	  Memory usage: 1%                IP address for eth1: 192.168.1.31
	  Swap usage:   0%
	
	  Graph this data and manage this system at https://landscape.canonical.com/
	
	Last login: Mon Mar 12 16:00:03 2012 from users.isi.deterlab.net
	ookskey@centos:~$ sudo curl --output /etc/dhcp3/dhclient-exit-hooks boss.isi.deterlab.net/downloads/client-update/Ubuntu1004-dhclient-exit-hooks
	  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                 Dload  Upload   Total   Spent    Left  Speed
	101  2943  101  2943    0     0  1573k      0 --:--:-- --:--:-- --:--:-- 2874k
	jhickey@centos:~$ sudo curl --output /usr/local/etc/emulab/findcnet boss.isi.deterlab.net/downloads/client-update/Ubuntu1004-findcnet
	  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                 Dload  Upload   Total   Spent    Left  Speed
	101  2331  101  2331    0     0  1300k      0 --:--:-- --:--:-- --:--:-- 2276k
	jhickey@centos:~$ sudo chmod a+rx /etc/dhcp3/dhclient-exit-hooks /usr/local/etc/emulab/findcnet
	jhickey@centos:~$ sudo chown root:root /etc/dhcp3/dhclient-exit-hooks /usr/local/etc/emulab/findcnet
	jhickey@centos:~$ 
	

Now the scripts are updated and I can take a snapshot.
