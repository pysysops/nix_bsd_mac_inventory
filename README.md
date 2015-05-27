This repository contains sample script to take information from different *nix operating systems and send it to [Device42](http://www.device42.com/) appliance using the REST APIs.

It has been forked and several modifications made to allow the scripts to be used to post inventory information to a generic RESTful(ish) API. 

Supported targets:

* Linux 
* BSD (OpenBSD and FreeBSD)
* OS X (tested on Mavericks)
* Oracle Solaris ( >= 11)
* AIX (tested on v 7.1)
    
### Requirements
-----------------------------
* python 2.7.x
* requests
* paramiko 
* netaddr
* This script works with Device42 5.10.2 and above
    
### Compatibility
-----------------------------
* Script runs on any OS capable of running Python 2.7.x
	
### Installation
-----------------------------
* Clone the repository or download an archive and un-compress somewhere: */opt/nix_bsd_mac_inventory/* for example.
* cd into the new directory and pip install:

	```Bash
	cd /opt
	git clone https://github.com/tjbirkett/nix_bsd_mac_inventory.git
	cd nix_bsd_mac_inventory
	pip install -r requirements.txt
	```
	
* Alternatively (and recommended) if you want everything contained within the application folder you can use virtualenv to create a python environment within the folder. This makes it easier if you're planning on packaging up the application to create a binary package.

	```Bash
	cd /opt
	git clone https://github.com/tjbirkett/nix_bsd_mac_inventory.git
	cd nix_bsd_mac_inventory
	virtualenv .
	./bin/pip install -r requirements.txt
	```

* Then use the python binary within the bin directory to run main.py or starter.py

	
### Usage
-----------------------------
* Run from main.py and use settings from inventory.cfg. Run against multiple targets, use multithreading and multiple credentials.
* Run from starter.py, use settings from inventory.cfg but specify (overwrite) single target, use_key_file, key_file, username and password from command line (take a look @ starter.py source)

### Note
----------------------------

By default, root has permissions to run dmidecode. If you are running auto-discover as non-root user, you would need following in your */etc/sudoers file.*

	%your-group-here ALL = (ALL) NOPASSWD:/usr/sbin/dmidecode

If this permission is missing, auto-discovery client would not be able to find out hardware, manufacturer and serial # etc.

You might also have to comment out Default Requiretty in */etc/sudoers file*.
