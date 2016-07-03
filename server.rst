===================
FTP Server (VSFTPD)
===================

VSFTPD Installation-
====================

VSFTPD stands for Very Secure FTP Daemon.To install VSFTPD issue following command->

::

	sudo apt-get install vsftpd -y

VSFTPD daemon commands-
========================

To start VSFTPD daemon-
-----------------------

::

	service vsftpd start 
		or
	/etc/init.d/vsftpd start


To stop VSFTPD daemon-
----------------------

::

	service vsftpd stop
		or
	/etc/init.d/vsftpd stop

To restart VSFTPD daemon-
-------------------------

::

	service vsftpd restart
		or
	/etc/init.d/vsftpd restart

To check if VSFTPD is running-
-------------------------------

::

	service vsftpd status
		or
	/etc/init.d/vsftpd status


Configuration file /etc/vsftpd.conf
====================================

Various aspects-

1- Anonymous FTP configuration-
-------------------------------
	By default vdftpd is not configure to allow anonymous download.To allow any user to download files enable following option

::

	anonymous_enable=YES

With above option any user can login to ftp server using 'ftp' or 'anonymous' as username and their email_id as password.

It is advisable not to allow anonymous user upload or edit file but if write is to be allowed edit options 

::

	write_enable=YES
	anon_upload_enable=YES

Then restart your ftp server.

2- Authenticated Mode configuration-
------------------------------------
	By default vsftpd is configured to authenticate system user and allow them to download and upload files.To enable file uploading and editing-

::

	write_enable=YES
	
To restrict user to edit its home directory through which user logged in-
--------------------------------------------------------------------------
	Enable the following options-

::

	chroot_local_user=YES
	chroot_list_enable=YES
	chroot_list_file=/etc/vsftpd.chroot_list


1. If *chroot_local_user* is set to NO and *chroot_list_enable* is set to YES, you may provide a list of local users who are placed in a chroot() jail in their home directory upon login.This list of user is kept in a file and name is supplied to *chroot_list_file* option. Above, user list is created in file named vsftpd.chroot_list.


2. If *chroot_local_user* is set to YES then meaning of *chroot_list_enable* is slightly different. In this case, the list becomes a list of  users  which  are NOT  to be placed in a chroot() jail.  By default, the file containing this list is */etc/vsftpd.chroot_list*, but you may  over‐ride this with the *chroot_list_file* setting.

Warning: This  option  has security implications, especially if the users have upload permission, or shell access. Only enable if you know what  you  are doing.  Note that these security implications are not vsftpd specific. They apply to all FTP daemons  which  offer to put local users in chroot() jails.



Add user to ftp server->
-------------------------

Recommended that make a separate for ftp users (let's say group is ftpuser)

::
	
	sudo groupadd ftpuser

Add a dummy shell to /etc/shells (say- */usr/sbin/nologin*) to restrict shell access.

*Case 1*- Give a particular user full access i.e. Download, Upload or Editing issue following command-

::
	
	sudo useradd -d /home/ftp -g ftpuser  -s /usr/sbin/nologin user1

Above commands creates a user with username user1, home directory /home/ftp, no shell access.
Assign a password with-

:: 
	sudo passwd user1

Now you will be prompted for new password.

For full access apply file permissions as-

::
	sudo chown -R user1 /home/ftp
	sudo chmod 755 /home/ftp 

*Case 2*- Give read permission only to another user (say user2) while user 1 has all permission

::
	
	sudo useradd -d /home/ftp -g ftpuser -s /usr/sbin/nologin user2
	sudo passwd user2
	
Now since it belongs to group ftpuser it will have read and execute permission but not write permission.

*check directory owner after adding any user to same home directory*

3. To run FTP as standalone (recommended)-
--------------------------------------------
	Enable following option

::

	listen=YES
	listen_ipv6=NO

These both options cannot be simultaneously yes.

4. Enable active or passive mode-
---------------------------------
To enable active mode set-

::
	
	connect_from_port_20=YES

To enable passive mode

::

	pasv_enable=YES
	pasv_min_port=*number_not less than 1024*
	pasv_max_port=*number not exceeds 65535*







