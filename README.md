windows-shares-migration
========================

Couple of scripts to migrate windows shares from one server to another

===! ATTENTION: for this script to work correctly SetACL is needed

===! It is awesome tool by Helge Klein.

===! You could get it here: http://helgeklein.com/setacl/ .

===! Download executables for 32-bit and 64-bit architectures and
place them into the same folder with those scripts.

===! You should name them like this: SetACL32.exe and SetACL64.exe

===! ALSO you would need some advanced notepad like "Notepad++". You could get it here: http://notepad-plus-plus.org/

Usage
=====

.\shares_backup.vbs - launch on old server (from which shares are going to migrate)

.\shares_restore.vbs - would be launched on new server during shares_create.cmd execution

.\own_shares.cmd - launch on old server (from which quotas are going to migrate) to take
ownership on shared folders before copying/moving them

.\shares_copy.cmd - launch on old server (from which quotas are going to migrate). 
Example: .\shares_copy.cmd \\new-server\d$

.\shares_create.cmd - launch on new server (to which quotas are going to migrate)

Manual
======

A) Run shares_backup.vbs on server from which you are willing to move shares. It will generate 5 files:

 * own_shares.cmd - batch file with commands to take ownership on shared folders to be sure you could
copy them;

 * shares.txt - contains shares list with ACL;

 * acllist.lca - contains NTFS ACL of shared folders (it's generated by SetACL and would be used by it);

 * shares_copy.cmd - batch file with commands to copy shared folders to a new server;

 * shares_create.cmd - batch file with commands to create shares on a new server;

B) You may want to launch own_shares.cmd to take ownership of a shared folders before copying/moving
them.

C) You should copy (or move) shared folders to a new server, you could do it with shares_copy.cmd.

D) Next you need to copy entire folder with scripts to a new server and perform next steps there. 

E) Edit path to shared folders in file shares.txt and acllist.lca. It would be better if you do that
with some advanced notepad like "Notepad++" for example, because it would preserve file codepage.

DO NOT USE MICROSOFT NOTEPAD! IT WOULD DEFINITELY SCREW UP CODEPAGE OF FILE.

F) Now you should launch shares_create.cmd on new server and patiently wait for it to do it's magic.

G) PROFIT!
