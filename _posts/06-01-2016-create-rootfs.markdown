---
layout: post
title: Setup the environment - Create the rootfs
modified: 2016-01-06
categories:
description:
tags: []
image:
  feature: main-background.jpg
  credit: 7themes
  creditlink: http://7-themes.com/7025787-brown-wallpaper-background-dekstop.html
comments:
share:
---

In this post I will describe the steps to be made in order to create a
rootfs in order to boot a VM (virtual machine) using qemu. The main goal
that we want to achieve be doing this is to create an environment where
the host machine is the one running ceph and the VM is the client.

In order to boot a VM using qemu we need 2 things:

	* a root filesystem - an image that contains the structure of
	  folders and subfolders used be a linux system

	* a kernel image corresponding with our needs - we created this in
	  the last tutorial


In order to complete the entire setup, my mentor for this project
provided me with some notes that he took when creating his setup. Those
notes suggested the fact the I should use a script found in the ceph
project in 'src/script/build_debian_image.sh'. Unfortunately, the script
in question was deleted by in some previous commit and currently it is
no longer in ceph.

To retrieve this script I have used git and its powerful commands. The
steps are described below:

cd ~/work/ceph
git rev-list -n 1 HEAD -- src/script/build_debian_image.sh

The last command should give you the hash of the commit in question
(that deleted the script). The hash is:
	c9a6e60eee8719472bcf71fffb20eb2557703f9d

Now we are ready to retrieve the file and place it back where it
belongs.

git checkout c9a6e60eee8719472bcf71fffb20eb2557703f9d^ -- src/script/build_debian_image.sh

Voila! We have the script back!

Now is the appropriate time to know that this script uses another one
that was also deleted in that same commit (I found it the hard way - by
running the script). So let's just recover the second script also :
network-from-cmdline

git checkout c9a6e60eee8719472bcf71fffb20eb2557703f9d^ -- src/script/network-from-cmdline

Now that we have everything that we need lets get to work:

cd ~/work/ceph
cd src/script
./build_debian_image.sh rootfs.img

This will create in the current directory a file an ext3 filesystem data
file describing a debian image. The script uses debootstrap to download
and install the necessary packages in the new rootfs so you should make
sure you have it installed:

sudo apt-get install debootstrap


If everything is ok you will now have a file called rootfs.img in your
current folder.

Unfortunately, I bumped into a problem exactly at the last step and the
output was this:

	+ umount /tmp/1227
	umount: /tmp/1227: device is busy.
			(In some cases useful info about processes that use
					 the device is found by lsof(8) or fuser(1))

It meens that the filesystem was created succesfully but the folder were
the file (rootfs.img) was mounted could not be unmounted. The step to
solve this are:

	* find out what are the processes using files from that folder:

	ioana@ceph:~/work/ceph/src/script$ sudo lsof /tmp/1227/
	lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
		  Output information may be incomplete.
		  COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF  NODE NAME
		  sshd    18908 root  cwd    DIR    7,0     4096     2 /tmp/1227
		  sshd    18908 root  rtd    DIR    7,0     4096     2 /tmp/1227
		  sshd    18908 root  txt    REG    7,0   475896 23639
		  /tmp/1227/usr/sbin/sshd
		  sshd    18908 root  mem    REG    7,0    51728 57368
		  /tmp/1227/lib/libnss_files-2.11.3.so
		  sshd    18908 root  mem    REG    7,0    43552 57401
		  /tmp/1227/lib/libnss_nis-2.11.3.so
		  sshd    18908 root  mem    REG    7,0    31616 57375
		  /tmp/1227/lib/libnss_compat-2.11.3.so

	* as we can see 'sshd' is the only process that restricts us from
	  unmounting the rootfs... so let's just terminate it.

	  ioana@ceph:~/work/ceph/src/script$ sudo kill -9 18908


	* finally unmount the rootfs:

	ioana@ceph:~/work/ceph/src/script$ sudo umount  /tmp/ 1227
	ioana@ceph:~/work/ceph/src/script$

	* check if everything is ok:

	ioana@ceph:~/work/ceph/src/script$ file rootfs.img
	rootfs.img: linux rev 1.0 ext3 filesystem data,
	uuid=7a3dd817-e960-400e-b5d3-69072b08aae3 (large files)
	ioana@ceph:~/work/ceph/src/script$ du -sh rootfs.img	689m    rootfs.img

Et voila! We have our own root filesystem that we are going to use to
boot our virtual machine in some next tutorial.





