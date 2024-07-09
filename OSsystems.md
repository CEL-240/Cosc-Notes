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
















