==================
FTP 
==================

Basics of FTP-
==============

FTP is file transfer protocol. It works on two ports->
1- For sending commands (default port number 21)
2- For transfering data files ( default port number 20)

The above port numbers can be changed as per administrator's concern.

WHY two separate ports ?
========================

The reason for creating two separate ports is that commands are generally smaller in size while there may be large size data files. If we were using single port the user would have to wait for the data file to get transferred to issue another command. So when user wants to issue a command it is transferred on port 21 and file transfer takes place on port 20.

WHAT do we need for ftp communication
=====================================

1.  FTP Client
2.  FTP Server
3.  Username for login to server
4.  Password

Two Modes of FTP communication-
===============================
	The way FTP client and server communicate are as follows-

1.   Active Mode
----------------
	In active mode, the client establishes the command channel (from client port X to server port 21) but the server establishes the data channel (from server port 20 to client port Y, where Y has been supplied by the client).


The sequence that takes place is as follows-

* Client opens up command channel from client port X to server port 21.
* Client sends PORT Y to server and server acknowledges on command channel.
* Server opens up data channel from server port 20 to client port X.
* Client acknowledges on data channel.

2.   Passive Mode
------------------
	In passive mode, the client establishes both channels. In that case, the server tells the client which port should be used for the data channel.

Passive mode is generally used in situations where the FTP server is not able to establish the data channel. One of the major reasons for this is network firewalls. While you may have a firewall rule which allows you to open up FTP channels to ftp.microsoft.com, Microsoft's servers may not have the power to open up the data channel back through your firewall. Such condition occur when you are in local network behind a NAT (network address translator). Although you allow data tranfer through your firewall, it may be blocked on your default gateway.

Passive mode solves this by opening up both types of channel from the client side.The following sequence of event occurs->

* Client opens up command channel from client port X to server port 21.
* Client sends PASV (use passive mode) to server on command channel.
* Server sends back (on command channel) PORT Z after starting to listen on that port.
* Client opens up data channel from client Y to server port Z.
* Server acknowledges on data channel.


Note-
-----

*-  The port X, Y and Z  are user ports ranging between 1025-65535.*

*-  Server may operate on port numbers other than 20 and 21.*
