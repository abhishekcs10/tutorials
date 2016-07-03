========================
Generating SSH key pair
========================

The SSH key pair generates a public and private key pair that is used for communication over the internet in in secured manner by encrypting the message.

How it works
=============

The Sender(S) and Receiver(R) both generates a key pair.Let,
SU=Sender Public Key
SK=Sender Private Key
RU=Receiver Public Key
RK=Receiver Private Key

1. The sender encrypts the message with its own private key (*call it M1*) so that the message can decrypted using sender's public key. This way it is authenticated that *S* has sent the message.
2. Then the sender encrypts the message *M1* with receiver's public key (*call it M2*) so that it can only be decrypted using receiver's private key.This way confidentiality of the message is confirmed.
3. Now on the receiver side the message *M2* is first decrypted using receiver's private key (RK) and message *M1* is obtained. After that *M1* is decrypted using sender's *S* public key *SU* and thus original message is obtained. 

Generating keys pair
====================
First verify that you already don't have ssh key pair generated. To check existing key pair use following commands-

::

	cd ~/.ssh
	ls

If the listing of file contains any *.pub* file then that file is contains your public key and other file contains your private key.
If you don’t have these files (or you don’t even have a .ssh directory), you can create them by running a program called ssh-keygen , which is provided with the SSH package on Linux systems.

To generate key pair simply run following command

::

	ssh-keygen

First it confirms where you want to save the key ( .ssh/id_rsa ), and then it asks twice for a passphrase, which you can leave empty if you don’t want to type a password when you use the key.

To view your public key -

::
	
	cat ~/.ssh/id_rsa.pub

*id_rsa.pub* is file created by ssh-keygen command and contains your public key while the other file in directory will contain your private key.



