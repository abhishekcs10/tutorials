============
FTP Client-
============

FTP Installation-
=================

FTP client comes pre-installed in most of the linux distributions. However, if your distro does not contains FTP client, install it using following command-

::

	sudo apt-get install ftp

*Most of the time I will be taking about command line based tools. There are other GUI tools like FileZilla which can be used for FTP client and Server management.*

Syntax-
=======

For FTP client the general syntax is -

::

	ftp [-options] hostname port

*Then you will be prompted for username and password.*

Some Important Options-
-----------------------

-4 	 Use only IPv4 to contact any host
-p 	 Use passive mode for data transfer.
-i	 Turns off interactive prompting during multiple file transfers.
-d 	 Enables debugging.


Some Important Commands in ftp after log in-
============================================

*binary*
				Set the file transfer type to support binary image transfer.

*bye*	
				Terminate the FTP session with the remote server and exit ftp.

*cd remote-directory*
				Change the working directory on remote machine

*close*	
				Terminate the FTP session with the remote server.

*delete remote-file*
				Delete the file remote-file on the remote machine.

*dir [remote-directory] [local-file]*
				Print a listing of the directory contents in the directory, remote-directory, and, optionally, placing the output in local-file. If interactive prompting is on, ftp will prompt the user to verify that the last argument is indeed the target local file for receiving dir output.  If no directory is specified, the current working directory on the remote machine is used.  If no local file is specified, or local-file is -, output comes to the terminal.
		
*get remote-file [local-file]*
				Retrieve the remote-file and store it on the local machine. If the local file name is not specified, it is given the same name it has on the remote machine, subject to alteration by the current case, ntrans, and nmap settings.  The current settings for type, form, mode, and structure are used while transferring the file.

*open host [port]*
				Establish a connection to the specified host FTP server.  An optional port number may be supplied, in which case, ftp will attempt to contact an FTP server at that port.  If the auto-login option is on (default), ftp will also attempt to automatically log the user in to the FTP server. 

