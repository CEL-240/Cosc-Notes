## day 1 10.5028.228 for ctf
less

 Pg Down; spacebar; CTRL+V; CTRL+F 	moves down one screen length
 Pg Up; CTRL+B 				move back up one screen lengthgrep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' StoryHiddenIPs | sort | uniq -c | sort -nr
 Down Arrow; ENTER; CTRL+N 		moves down one line at a time
 Up Arrow; CTRL+Y 			moves up one line at a time
 /pattern 				searches FWD for pattern ie: /logs
 ?pattern 				searches BACK for pattern ie: ?logs
 / 					repeats previous search
 q 					quit less
 man less 				for more optionsFind all dmesg kernel messages that contain CPU or BIOS (uppercase) in the string, but not usable or reserved (case-insensitive)
grep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' StoryHiddenIPs | sort | uniq -c | sort -nr


locate

 searches database for linux native commands ie: # locate find



whereis

 searches for binary files, executables, and config files AND man
 page page directories [ /usr/share/man/* ];
 $whereis man ; $manpath
 does not search user directories: /home /* OR various other locations easily
 searched by `find' AND `locate' ie: #




Process Hierarchy

 Kernel
    |_____ init - 01
               |________ BASH
                           |__________ ps



psFind all dmesg kernel messages that contain CPU or BIOS (uppercase) in the string, but not usable or reserved (case-insensitive)

 ps -u Jim 		IDs processes use by user: Jim
 ps --forest 		show complete process tree with parent child relationships
 ps -u Jim –-forest 	show for user: Jim only
 ps u U Jim –-forest 	owned by user: Jim
 ps aux 		a == shows all procs running on system
 			u == users running the proc
 			x == CMDs that ran the procs.



top

 IDs procs using most CPU or memory
 top -k <PID>		kills process
 top -P 		sorts by CPU usage
 top -M 		sorts by Memory usage



free

 Measures Memory usage
 - /+ shows actual memory usage by programs (more useful them the Mem: line)
 Swap: disk space used when RAM space is not available



dmesg

 Kernel Ring Buffer (log file generated soley in Memory) good for diagnosing driver & hardware issues
 dmesg | less
 dmesg | grep sda ID kernel messages concerning only 1st hard disk (sda)



Regex

 Wildcards
 	? 		matches 0 or more occurances (may or may not occur) +
	. 		any single character
	*		any chars
	^		represents start of string
	$		represents end of string
	[a-zA-Z0-9]	can contain any within range [..]
	[1..99] 	denotes range from 1 to 99
	{1,3} 		can contain as few or as many of {..,..}
	[1-3]*		denotes one or more matches to [1-3]
	.*		used to match any single character one or more times
	\. 		matches the actual dot "."
	\?		matches the actual question mark "?"
	+		matches 1 or more occurances
	(….)		denote sub-expressions
	"cat|dog[fish]" can match either cat fish OR dog fish
	$touch \{cat,dog,flying,running}fish
	$ls -1 | grep "cat|dog[fish]"
	| 		matches either (….) | (….) essentially an "OR"



find

 find -name		denotes case-sensitive file
 find -iname 		denotes case-insensitive file
 find -ilname 		" and symbolic linked files
 find -inum ##### 	searches for file w/ inode "#####"
 find -size 		denotes file of "x" size
 find -size 10c 	finds file of size exactly 10 bytes
 find -size +10M -20M 	finds file of size greater than 10MB and less than 20MB
 find -size -1G 	finds file of size less than 1GB
 find -group 		denotes belonging to group "name"
 find -gid 		denotes files belonging to group ID "###"
 find -user		denotes files belonging to user: "name"
 find -uid 		denotes files belonging to user ID: "###"
 find -maxdepth 	searches to designated depth only for designated files
 find /* 		starts recursive search at "/"
 find /* -type d	" for directories ONLY
 find /* -type f	" for files ONLY
 find /* -type p 	" for named-pipes ONLY
 find /* -type l	" for symbolic links ONLY
 find /* -type s	" for sockets ONLY
 find / -type s -exec echo {} 2>/dev/null ; | grep domain* finds socket files
 find -name \*.txt 	searches from pwd recursively for files ending in ".txt"
 find -atime 3 		accessed in last 3 days
 find -ctime 2		changed 2 days ago
 find -mtime 2		modified 2 days ago
 find $HOME -mtime 0 	searches for files modified in last 24hrs in current-user home-dir

 find -cmin -30		changed last 30 minutes
 find -amin -60		accessed last hour
 find -mmin -60		modified in last hour
 find -empty		searches for empty files ONLY
 find -executable	Matches files which are executable and directories which are searchable
 find -exec		execute CMD;true is "0" status returned

 find /var/log/ -iname *.log -exec ls -al {} 2>/dev/null \;

            		finds all .log files in directory: /var/log/ and lists them all

 find -path		searches in designated path
 find -ls		lists files that are found
 find -print		print output and automatically adds new-line
 find -printf \n	prints output followed by new-line
 find -prune		searches for files recursively but avoids descending into dirs
 find -perm		denotes files with designated permissions level

 find / -perm /4000 -uid 0 -ls 2>/dev/null

            		finds all SUID files owned by "root" and displays them

 find / -perm -2 -type f 2>/dev/null

            		finds all GUID world files

 find / -perm -2 ! -type -l -ls 2>/dev/null

            		finds all GUID world files that are not links

 find / ! -path "/proc/*" ! -path "/root/*" -perm -2 -type -f -ls 2>/dev/null

            		finds all world files not in directories: /proc OR /root

 find / -perm /2 -ls 2>/dev/null

            		finds files writable by anyone




Cut



cut -d: -f1         displays only portion of line before 1st instance of delimiter ``:''
cut -d: -f1-        " and any following strings up to the very next instance ``:''
cut -d: -f1- -s     " " but don’t print any lines not containing delimiter ``:''
cut -f3             displays only the 3rd field delimited by space
cut -f2-4           displays only fields 2 through 4 delimited by space
cut -c3-10          displays only the 3rd through 10th characters of each line




NOTE: Tabs are counted as single spaces on a line; both are counted as single characters






Awk



awk -F: '{print $1}'         displays 1st field delimited by a ":"
awk '{print $2}'             displays 2nd field, delimited automatically by space
awk '{print $0}'             displays all string data that matches

awk -F: '($3 == 0) {print $1}' /etc/passwd
                            displays 1st field (username) IF the 3rd field (UID) is equal to "0"
awk '{print $NF}'           displays only the last field of every line






grep



grep -c                 counts number of lines that match
grep -r ; grep -R       recursive
grep -f                 files only
grep -E                 regular expressions (GNU)
grep -o                 displays ONLY matches of regex / not whole line
grep -i                 case-insensitive match
grep -l                 displays only file name (full path) of matching regex
grep -C#                in context of match (# of lines before and after)
grep -A#                displays # of lines after matching regex
grep -B#                displays # of line before matching regex
grep -P                 uses Pearl regular expressions (non-GNU)
grep ""                 shell quoting (BASH interpretable)
grep ''                 shell quoting (NOT BASH interpretable)






Command Chaining Operators:



&   --Sends process to background (so we can run multiple process parallel)
;   --Run multiple commands in one run, sequentially.
 \  --To type larger command in multiple lines
&&  --Logical AND operator
||  --Logical OR operator
!   --NOT operator
|   -- PIPE operator
{}  --Command combination operator.
    [ -f 99.txt ] || { echo " does not exist"; touch 99.txt; }
()  --Precedence operator



Basic BASH Scripts:
Conditional Expressions Source: https://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html





Conditionals



-e          file exists ?
-f          file exists, and is regular file ?
-d          file exists, and is a directory ?
-s          file exists, and is NOT empty ?
-x          file exists, and IS executable ?
-w          file exists, and is writable by me ?
-gt >       is greater than
-lt <       is less than
-ge         is greater than or equal to
-le         is less than or equal to
-eq ==      is equal to
-ne !=      is NOT equal to






Bash Script using conditional " -f " :



shell_env                       #!/bin/bash
[Conditional]                   if [[ -f /etc/password ]]; then
Command                             echo "/etc/password file exists";
[Conditional]                   elif [[ ! -f /etc/password]]; then
Command                             echo "/etc/password file doesn’t exists";
                                fi






Bash Script using conditional " -w " :



shell_env                       #!/bin/bash
[Conditional]                   if [[ -w /etc/passwd ]]; then
Command                             echo "/etc/passwd is writable by me";
[Conditional]                   elif [[ ! -w /etc/passwd ]]; then
Command                             echo "/etc/passwd file isn’t writable by me";
                                fi






Bash Script using conditional " BOLEAN " :



$(( )) expands "C" arithmetic expressions, but instead of returning a BOLEAN value, it
returns the math.

shell_env                       #!/bin/bash
[Conditional]                   if [[ 3129 == $(( 15645/5 )) ]]; then
Command                             echo "math checks out";
[Conditional]                   elif [[ 3129 != $(( 15645/5 )) ]]; then
Command                             echo "math is no good";
                                fi






When to use ( == vs. -eq ) & ( != vs -ne ) :



when comparing a string you should never use -eq OR -ne, instead use == OR !=
when comparing a string integer either is fine to use .. ex:

if [[ banana == apple ]]; then
echo "banana IS an apple"
else
echo "banana is NOT an apple";
fi
= banana is NOT an apple

if [[ banana -eq apple ]]; then
echo "banana IS an apple";
else
echo "banana is NOT an apple";
fi
= banana IS an apple

if [[ banana != apple ]]; then
echo "banana is NOT an apple";
else
echo "banana IS an apple";
fi
= banana is NOT an apple

if [[ banana -ne apple ]]; then
echo "banana is NOT an apple ";
else
echo "banana IS an apple";
fi
= banana IS an apple

if [[ 41 -eq 42 ]]; then
echo "41 is 42";
else
echo "41 is NOT 42";
fi
=41 is NOT 42

if [[ 41 == 42 ]]; then
echo "41 is 42";
else
echo"41 is NOT 42";
fi
=41 is NOT 42

if [[ 41 -ne 42 ]]; then
echo "41 is NOT 42";
else
echo "41 is 42";
fi
=41 is NOT 42

if [[ 41 != 42 ]];then
echo "41 is NOT 42";
else
echo "41 is 42";
fi
=41 is NOT 42






Aliases



alias rm='rm -i'                    creates alias to confirm removal
alias vim='nano'                    creates an alias for `nano'
alias gedit='nano'                  "
alias vi='nano'                     "
alias x='cat etc/passwd'            creates an alias for Command: cat/etc/passwd
alias y=$(cat /etc/shadow)          " cat /etc/shadow
alias ls='ls -al'                   creates an alias causing 'ls -al' to be run when 'ls' is used
\ls                                 negates the alias function, so we can run 'ls' without '-al'
alias -p                            view all aliases set (local and global)
unalias ls                          unaliases ls so it no longer resolves to 'ls -al'






Redirection Operators:



>                                   creates new file with STDOUT; if file exists, it is overwritten
>>                                  appends STDOUT to existing file; if file doesn’t exists, it is created
2>                                  creates new file with STDERR; if file exists, it is overwritten
2>>                                 appends STDERR to existing file; if file doesn’t exists, it is created
&>                                  creates new file with STDOUT+STDERR; if file exists, it is overwritten
<                                   use contents of file as STDIN
<<                                  accepts ASCII text as STDIN on the following lines
<>                                  specified file is used as both STDIN and STDOUT






Sed



sed '/.dll/{x;p;p;p;x}' -i document.txt
    directly alters document.txt by adding 3 empty lines before the designated regex (.dll)

sed '/stuff/G;/stuff/G' -i document.txt
    directly alters document.txt by adding 2 empty lines after the designated regex (stuff)

sed -i -e 's/ANCHOVIES/SAUSAGE/g' pizaster.htm
            replaces every instance of "ANCHOVIES" with "SAUSAGE" on pizaster.htm

sed -i -e 's/ANCHOVIES//g' pizaster.htm
            removes every instance of "ANCHOVIES" on pizaster.htm

sed -i '/^#/d' /etc/hosts.allow
            removes all lines starting with "#" from file /etc/hosts.allow

# day 2 excersises 

grep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' StoryHiddenIPs | sort | uniq -c | sort -nr #finds ips in a file and sorts them by how many time they appear 

awk -F: '$3 > 3 && $7 == "/bin/bash" {print $1}' $HOME/passwd > $HOME/SED/names.txt ##uses awk to find only the names of system and user accounts that arent UID 0-3 that only display bash shell as their default shell 


# sed 
a stream editor utility
sedexplain.txt> 
-e expression for many sed patterns
s substitution for start pattern
g global lowercase
d deletes
s eis end of the line 
sed -e 's/chicken/hmburger/g' -e 's/pepperoni/sausage/' pizza.txt
words go between '//'
sed -e 's/chick/ham/g' -e 's/pep/saus/' lel.txt

# commmand substitution
#!/bin/bash
A=$(cat /etc/passwd)
echo $A #this makes A the cat etc passwd 

A=$(find /usr/bin -name passwd)
echo A$

if [[ banana == apple ]];
	then echo "banana is n apple"
else echo "banaan is not an apple";
fi

Sort

sort                sorts content according to position on the ASCII table
sort -n             sorts content numerically
sort -u             sorts content uniqely
sort -nr            sorts content numerically reversed
sort -t +
sort -k 2,4         sorts 1st by content in the 2nd column, then by content in the 4th column






Uniq

uniq                sorts content uniqely
uniq -c             sorts content uniqely with a count reading

dmesg | egrep 'CPU|BIOS' |egrep -iv 'usable|reserved' | cut -d ] -f '2-' # finds dmesg kernel messages that have cpu or bios and dont hVE usable or reserved

sed -n '/\/bin\/sh$/!{/\/bin\/false$/!p}' $HOME/passwd > $HOME/PASS/passwd.txt ##using sed, write all lines from homa passwd into pass passwd that dont end in bin/sh or bin/false

cat /etc/passwd | sort -k4 -t: -n | head -10 | tail -1 | cut -d: -f6 | md5sum | cut -d" " -f1 ## sorts passwd file by guid field and gets the 10th entrys md5, outputs only the md5 hash

files=$(find /bin /sbin /usr/bin /usr/sbin -type f -executable 2>/dev/null | sort | sed -n '10p'); [ -n "$files" ] && md5sum "$files" | cut -d" " -f1
##
ind all executable files under the following four directories:

    /bin
    /sbin
    /usr/bin
    /usr/sbin

Sort the filenames with absolute path, and get the md5sum of the 10th file from the top of the lis
##

find "$HOME" -type f -name "*.bin" -exec dirname {} \; | sort -u  
##
sing find, find all files under the $HOME directory with a .bin extension ONLY.
Once the file(s) and their path(s) have been found, remove the file name from the absolute path output.
Ensure there is no trailing / at the end of the directory path when outputting to standard output.
You may need to sort the output depending on the command(s) you use.
##

mkdir 11{23,34,45,56} #brace expansion makes new dirs such as 1123 

mkdir $HOME/1123
cd $HOME/1123
touch {1,2,3,4,5,6~,7~,8~,9~}.txt
##
makes new .txt files
##

find $HOME/1123 -name *.txt -not -name *~* -exec cp {} $HOME/CUT \;
##copies all files from 1123 with .txt but no ~s and puts them in cut 

find /var -empty -printf "%i %f\n" ## fidns all empty files from var and prints their inode and filename seperated by newlines 
-inum 4026532575 ## finds file with the inode number 

ls -l $HOME/CUT | cut -d. -f1- -s | cut -d: -f2 | cut -d' ' -f2 > $HOME/CUT/names ##shows all name with extensions nut mo directories, written to a names file and omits names filename from output 

grep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' StoryHiddenIPs | sort | uniq -c | sort -nr ##greps only ips in a file and sorts them uniquely by how many times they appear

awk -F: '$3 > 3 && $7 == "/bin/bash" {print $1}' $HOME/passwd > $HOME/SED/names.txt ##extracts only the names of all system and user accounts that are not uid 0-3, only displays those with bin bash as dewf shell, output to a file names .txt 




## practice test
Create a script that will perform the following actions:

    Replace every instance of 'cat' in "infile" with 'dog'.
    Replace every instance of 'Navy' in "infile" with 'Army'.
    Replacements are case-sensitive.
    Write the output to the file specifed by the variable 'outfile'.


function q1()
{
  #Valid Variables are:
  infile=$1
  outfile=$2
  sed -e 's/cat/dog/g' -e 's/Navy/Army/g' $1 > $2
}


Create a script that will print to standard output all user names from the /etc/passwd file.

function q1()
{
  cut -d: -f1 /etc/passwd | sort -r
}


Create a script that will perform the following actions:

    Print to standard output all usernames from the file path specified by the parameter filename sorted ascending numerically by user id.
    The file will be in the format of /etc/passwd

function q1()
{
  #Valid Variables are:
  filename=$1
  #!/bin/bash

if [ -z "$1" ]; then
  echo "Usage: $0 <filename>"
  exit 1
fi

Create a script that will perform the following actions:

    Print to standard output the total number of files in the directory specified by dirname.
    If the directory does not exist, print 'Invalid Directory'
    The count excludes the '.' and '..' pseudo-directories.

function q1()
{
  #Valid Variables are:
  dirname=$1
  [ -d "$1" ] && find "$1" -maxdepth 1 -type f | wc -l || echo "Invalid Directory"

}

Create a script that will perform the following actions:

    Delete all files contained in the directory specified by dirdel
    Also delete the directory specified by dirdel

function q1()
{
  #Valid Variables are:
  dirdel=$1
  rm -rf $1
}

Create a script that will perform the following actions:

    Create a file specified by the name newfile.
    Set the file modified date to the value specified in filedate and time to '1730'. NOTE: filedate contains only a valid date in YYYYMMDD format, not a time.

function q1()
{
  #Valid Variables are:
  newfile=$1
  filedate=$2
  touch -t "$2"1730 $1
}


Copy all lines from the file specified by src variable to the file specified by dst variable which DO NOT contain the text specified by match variable.


function q1()
{
  #Valid Variables are:
  src=$1
  dst=$2
  match=$3
  grep -v "$match" "$src" > "$dst"

}


Terminate the process that has the randomly assigned name specified by procname variable. procname does not contain path information.

function q1()
{
  #Valid Variables are:
  procname=$1
  pkill $1
}


Create a sorted full-path list of all files in the directory dirpath that were modified within the previous day. Directories should not be included in the output. Print the list to the screen, one item per line.

NOTE: The full paths to files should be in your output. (i.e. /etc/passwd would be included)

NOTE: Directory entries should not be included. (i.e. /etc would NOT be included)

function q1()
{
  #Valid Variables are:
  dirpath=$1
  find "$dirpath" -type f -mtime -1 -print | sort
}



cont='cat $fname'
if [[ $cont -lt 10 ]] ; then
	echo single digit 
elif [[ $cont -lt 100 ]] ; then
	echo double digit
 else Error 
 fi 

tar -czf


## SAM

#1
Create a script that will perform the following actions:

    Print all lines from the file specified as "filename" file to standard output that are not blank lines and are not comments.
    Comments are lines which include a '#' as the first character.
    Do not print anything else to standard output for this question.
    The format of the input file will be similar to that of the /etc/hosts file.

function q1()
{
  #Valid Variables are:
  filename=$1
  #You code here
}

function q1()
{
  #Valid Variables are:
  filename=$1
  #You code here
  grep -vE "^\s*($|#)" "$filename"
}

----------------------------------------------------------------------------------------------------------
#2


Create a script that will perform the following actions:

    Locate all files that end in ".log" in the specified directory by "logs"
    Create an archive of those files in a gzipped tar ball
    Store the gzipped tar ball as the file name specified in "archive"

function q1()
{
  #Valid Variables are:
  logs=$1
  archive=$2
  #Your code here
}

function q1()
{
  #Valid Variables are:
  logs=$1
  archive=$2
  #Your code here
  tar -czf "$archive" -C "$logs" $(find "$logs" -type f -name "*.log" -printf "%P\n")
}










---------------------------------------------------------------------------------------------------------------
#3



Create a script that will perform the following actions:

    Locate all files in the directory "searchdir" that contain the case insensitive text "CRITICAL".
    Write all the filenames with path into a file specified by argument "output".

IMPORTANT NOTE: The contents of the file are what matter, not the filename. No filenames will contain critical.

function q1()
{
  #Valid Variables are:
  searchdir=$1
  output=$2
  #Your code here
}

function q1() {
  # Valid Variables are:
  searchdir=$1
  output=$2

  # Your code here
  find "$searchdir" -type f | while read -r file; do
    if grep -qi "CRITICAL" "$file"; then
      echo "$file"
    fi
  done >> "$output"
}




----------------------------------------------------------------------------------------------
#4




Create a script that will perform the following actions:

    Given a space separated list of directories in "dirlist", your code will obtain the total number of files in all the directories. Subdirectories will NOT be included in the total.
    Print to standard output the total number of files

function q1()
{
  #Valid Variables are:
  dirlist=$1
  #You code here
}

function q1()
{
  dirlist=$1

  total_files=0

  for dir in $dirlist; do
    if [ -d "$dir" ]; then

      num_files=$(ls -l "$dir" | grep -c '^-')
      # Add the count to the total
      total_files=$((total_files + num_files))
    else
      echo "Directory $dir does not exist."
    fi
  done
  echo $total_files
}


------------------------------------------------------------------------------------
#5





Create a script that will perform the following actions:

    Delete all files contained in the directory specified by "dirdel"
    Do not delete the directory specified by "dirdel"

function q1()
{
  #Valid Variables are:
  dirdel=$1
  #Your code here
}

function q1()
{
  # Valid Variables are:
  dirdel=$1
  find "$dirdel" -mindepth 1 -type f -delete
}





-----------------------------------------------------------------------------------
#6


Create a script that will perform the following actions:

    Create a file specified by the name contained in parameter "newfile"
    Set the modified date of the file to June 14, of the current year
    Set the modified time to the file to 0830

function q1()
{
  #Valid Variables are:
  newfile=$1
  #Your code here
}


function q1()
{
  # Valid Variables are:
  newfile=$1
  touch "$newfile"
  current_year=$(date +%Y)
  touch -t "${current_year}06140830" "$newfile"
}




--------------------------------------------------------------------------------------
#7


Create a script that will perform the following actions:

    Read the file specified by "filename" and perform an action based on the contents of the file
    If the contents of the file are "abc", print "123" to standard output
    If the contents of the file are "def", print "789" to standard output
    If the contents of the file are "xyz", print "000" to standard output
    If the contents of the file are not "abc", "def", or "xyz", print "Error" to standard output

function q1()
{
  #Valid Variables are:
  filename=$1
  #Your code here
}



function q1()
{
  # Valid Variables are:
  filename=$1

  # Your code here
  content=$(<"$filename")

  
  if [[ $content == "abc" ]]; then
      echo "123"
  elif [[ $content == "def" ]]; then
      echo "789"
  elif [[ $content == "xyz" ]]; then
      echo "000"
  else
      echo "Error"
  fi
}


--------------------------------------------------------------------------------------
#8




Create a script that will perform the following actions: Copy all lines from the file specified by "src" to the file specified by "dst" which contain the text specified by "match"

function q1()
{
  #Valid Variables are:
  src=$1
  dst=$2
  match=$3
  #Your code here
}


function q1()
{
  #Valid Variables are:
  src=$1
  dst=$2
  match=$3
  #Your code here
  cat $src | grep $match > $dst
}




--------------------------------------------------------------------------------------
#9


Create a script that will perform the following actions:

    Terminate the process that has the name specified by 'var'.
    The name of the process in 'var' varies and will change each time the application is run

function q1()
{
  #Valid Variables are:
  var=$1
  #Your code here
}



function q1()
{
  #Valid Variables are:
  var=$1
  #Your code here
  pkill "$var"
}


--------------------------------------------------------------------------------------
#10



Create a script that will perform the following actions:

    Given a directory specified by "dirpath" create a sorted list of all files in the directory that were modified within the previous hour.
    Ensure that the full path to each file is used for the sort and is included in the output.
    The list should include all files in the specified directory and any subdirectories.
    Print this list to the screen, one item on each line.

function q1()
{
  #Valid Variables are:
  dirpath=$1
  #Your code here
}

function q1()
{
  #Valid Variables are:
  dirpath=$1
  #Your code here
  find "$dirpath" -type f -mmin -60 -printf "%p\n" | sort
}












