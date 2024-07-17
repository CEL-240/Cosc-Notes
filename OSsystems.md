## day 1 
im number 7 
my ip is 10.50.33.31 xfreerdp /u:student /v:10.50.33.31 -dynamic-resolution +glyph-cache +clipboard
http://10.50.22.197:8000/
M24005
password
KYGA-M-005
ssh -JX student@10.50.xx.xx garviel@10.7.0.6

--------------------------------------------------
https://os.cybbh.io/public/os/latest/index.html

/media/Bibliotheca/Bibliotheca_duo/.warp2/.warp5/warp5/.warp3/warp2/.secrets

Registry" - for registry locations, "FileSystem" for file system locations are the only providers we will use

-----------------------------------------------

## windows registry

manipulation is doen with regedit.exe

3.3 Registry Manipulation with PowerShell


Certain Root Hives are loaded automatically into PSDrives (HKLM: and HKCU:); navigation of the registry is very similar to folder⇒file

Minimum commands to know
* Query

Get-ChildItem cmdlet gets the items in one or more specified locations.

Get-ItemProperty cmdlet gets the items in one or more specified locations.

Get-Item cmdlet gets the item at the specified location. It doesn’t get the contents of the item at the location unless you use a wildcard character (*) to request all the contents of the item.

* Modify

Set-ItemProperty cmdlet changes the value of the property of the specified item. example, changing setting to :true or :false.

Remove-ItemProperty cmdlet to delete registry values and the data that they store.

* Create

New-Item cmdlet creates a new item and sets its value. In the registry, New-Item creates registry keys and entries.

New-Itemproperty cmdlet creates a new property for a specified item and sets its value. Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.
---------------------------------------------------------------------------------

Using the commands ls and grep, identify the number of directories in /etc/ that end in .d

 ls -l /etc/ | grep '^d.*\.d$' | wc -
 -------------------------------------------------------------------------

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
# runs everytime machine reboots
--------------------------------------------------------------------------

# What registry subkey runs every time the machine reboots? The flag is the full path, using PowerShell
HKCU:\Software\Microsoft\Windows\CurrentVersion\Run

--------------------------------------------------------------------------------------------------------------------

HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
# What registry subkey runs a single time, then deletes its value once the machine reboots? The flag is the full path, using PowerShell.
----------------------------------------------------------------------------------------------

# List entries in the "Run" registry key
Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"

## gives entries in keys, very important for persistence
===========================================================================

What is the suspicious value inside of the registry subkey that loads every time the "Student" user logs on?

wmic useraccount where name='Student' get sid # GETS THE SID FOR STUDENT 
========================================================================

# queries every user that connected to machine 
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersio
n\ProfileList" /s


dd if=/home/bombadil/mbroken bs=1 count=16 skip=446 | md5sum 
# gives first partition of MBR 

dd if=/home/bombadil/mbroken of=/tmp/bootstrap.bin bs=1 count=446
# gives boostrap

/sauron
91:2345:respawn:/bin/netcat -lp 9999
====================================================================
registry, startup folder, schtasks, powershell profiles, services 
====================================================================


if running a sysinternal tol and its cli  you need at the very end -acceptEULA


## review


REVIEW
------------------
!/ETC is a directory for configurations!
If something is a scheduled task, it will survive a reboot.

Systemd perstence
  /sbin/init
SysV persistence
  /etc/init

Sysinternals tools
  Procmon
  Autorun - keys, tasks (most useful)

Permissions Linux
  Execute in a directory - You can move into it
    If no permission set, then you cant go into it (cd <file>)
    Still interact with it with ls.
    SUID - The owner of the file, rather than the user running it
    GUID - The group that has access to the file.
    Sticky bit - is usually for shared directories. If I set the sticky bit on a directory, I am the only one that can delete it.

Zombie
  defunct process is a process that has completed execution
Orphan
  Gets addopted by int

Daemon
  Services
  Background processes
  It uses them as a method of persistence
  /> systemctl status
Linux Logging - /var/log, /etc/rsyslog.conf

Powershell Profiles
  Current User, Current Host
  Current User, All Hosts
  All users, Current Host
  All Users, All Host
$HOME - user's home path {/home/<user>

Windows Registry
  HKLM - contains system startup information
  HKCU - Current User, symbolically linked to HKU
  HKCC - stores current hardware profile
  HKCR - contains registered application information

Things to Look For:
  Mispelled file names that shouldnt be mispelled
  Something that should be a system level process, but has a high ppid
  Seeing multiple names for a process that should only be there once
  High PIDs for processes that shoulds be low

Format for the test:
  Something happened to the computer system.
  Check logs ## 
  Check for services, processes ##
  Check Powershell profiles for persistence (run through each one) ##
  Check the run keys ##
  Sysinternals tools
    use autorun ##
    use process explorer ##
  Check alternate data streams (refer to notes) ##
  Check services (can run executables) ##
  Check for scheduled tasks ##
  Linux boot
    Check the run levels ##
      /etc/inittab
      Check default runlevel ##
    Check Bash profiles ##
      Bashrc
      Bash_profile
    Systemd
    Sysv

