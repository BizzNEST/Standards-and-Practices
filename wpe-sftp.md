# How to SFTP into WPE(Wordpress Engine) Environment

This document will guide you through the process of using SFTP to connect to a WPE environment. Follow the steps below to establish a secure file transfer connection and manage files on your WPE system.

## Prerequisites

1. Access to WPE
2. Have FileZilla downloaded

## Process:

### Video Walkthrough: 
[Video Here](https://youtu.be/OaCLjHSJj-g)

### Step 1(WPE):

1. Sing in to WPE.
2. Navigate to the site and environment you want to SFTP into.
3. Go to Users and SFTP tab.
4. Select SFTP Users.
5. Select Create SFTP User.
6. Enter a username and password (remember the password, as it will be used again).

### Step 2(FileZilla): 

1. Open FileZilla.
2. Open Site Manager (top left corner).
3. Ensure the protocol is set to "SFTP - SSH File Transfer Protocol."
4. Enter the SFTP address in the Host field (provided where you created your SFTP user in WPE).
5. Enter the port number in the Port field (provided where you created your SFTP user in WPE).
6. Ensure Logon Type is set to "Ask for password."
7. Enter the SFTP username you created in WPE in the "User" field.
8. Click the blue Connect button.
9. You will be prompted to enter the password (the password created during the SFTP user setup).
10. You may see a message stating, "The server's host key is unknown. You have no guarantee that the server is the computer you think it is." This is normal; select OK.
11. Wait a moment, and you should be connected to the server.
