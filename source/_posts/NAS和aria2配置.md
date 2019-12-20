title: NAS配置
author: yaoxingwei
date: 2019-07-11 11:27:50
tags:
---
# 1. Ubuntu环境设置
## 1. git config

	sudo apt install git
	git config --global user.name "xxx"
	git config --global user.email "xxx@xxx.com"

## 2. generate ssh key
	ssh-keygen -t rsa -C "xxx@xxx.com"
    
## 3. install samba
	sudo apt install samba

## 4. edit samba config file for win share
config file path: /etc/samba/smb.conf

	[share]
	comment = t610 samba share
	path = /home/yxw/share
	browseable = yes
 	writeable = yes
	#guest ok = no
	public = yes
	#security = share
	#admin user = root
	create mask = 0777
	directory mask = 0777
	forceuser = root
	forcegroup = root
	display charset = UTF-8
	unix charset = UTF-8
	dos charset = UTF-8
    
> Note: access samba path in windows: \\\192.168.xxx.xxx\share
    
 ## 5. set nfs for linux share
	sudo apt-get install nfs-kernel-server
	sudo vi /etc/exports
    	/home/share/nfsroot *(rw,sync,insecure,no_root_squash,no_subtree_check)
	sudo /etc/init.d/rpcbind restart
	sudo /etc/init.d/nfs-kernel-server restart
	sudo exportfs -r
	sudo mount -t nfs localhost:/home/share/nfsroot  /mnt	# test mount and access method