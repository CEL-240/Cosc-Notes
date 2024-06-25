## day 1 
# login: xfreerdp /u:student /v:10.50.23.80 -dynamic-resolution +glyph-cache +clipboard
# run powershell ISE 
hit f8 for running a line and f for the whole script 
Get-Process | Format-list #processess and formats into a list 
get-help <whatever youu need help w> -Examples or -Detailed, #'s are comments, <> allow multiline comments 

# variables
$var = 1makes $var 1
$var | get-member shows methods and property
$var.getype().name shows just the value of the type table ITS IMPORTANT 
[string]$var + 'hello' gives 1hello

# automatic variables
$inout,$matches,$psitem are what well use 

# arrays
$myarray = 'hello', 12, (get-date), $false ##once you call $myarray its gives that stuff
$myarray.gettype().basetype.name
$myarray[0][1] gives hello the first thing and the second letter e 
$var += 1 makes var 2 because of the =
$newarray = @() YOU NEED AN @ TO GET AN EMPTY ARRAY ((1,2,3,4)(5,6,7,8)) makes 2 arrays 
$newarray += 1  appends 1 to an empty array

# pipeline
you pipe stuff with | 
get-process | get member | sort -property name 
get-process | get-member | where-object -property name -EQ ID
get-childitem 
set-alias edit notepad.exe makes the command edit open  notepad 

# what cmdlets print output to a screen?
Write-Warning.
Write-Error.
Write-Output.
Write-Host.

# What cmdlets can be used to create, modify, list, and delete variables?
et-Variable	Gets the variables in the current console.
New-Variable	Creates a new variable.
Remove-Variable	Deletes a variable and its value.
Set-Variable

# What cmdlet can be used, other than Get-Help, to find and list other cmdlets?
get-command 

# Find the cmdlet that is used to prompt the user for input.
read host

# Display a list of all running processes that start with the letter "s".
Get-Process | Where-Object { $_.Name -like "s*" }

# Find the cmdlet and its purpose for the following aliases:

gal = get-alias 

dir= get-childitem 

echo = write-output

? = where-object

% = foreach-object

ft = format-table 

# Display a list of Windows Firewall Rules.

Get-NetFirewallRule

# Create a new alias called "gh" for the cmdlet "Get-Help"
New-Alias -Name gh -Value Get-Help
# create a array that holds random number between 25 and 50 
$var1 = Get-Random -Minimum 25 -Maximum 51

# Create a variable called "var2" that holds a random number between 1-10.
$var2 = Get-Random -Minimum 1 -Maximum 11

# Create a variable called "sum" that holds the sum of var1 and var2.
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11
$sum = $var1 + $var2

# Create a variable called "sub" that holds the difference of var1 and var2.
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11
$sub = $var1 - $var2

# Create a variable called "prod" that holds the product of var1 and var2.
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11
$prod = $var1 * $var2

# Create a variable called "quo" that holds the quotient of var1 and var2.
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11
$quo = $var1 / $var2

# Replace the variables in text with their values in the following format:

"var1" + "var2" = "sum"

# Generate random values for var1 and var2
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11

# Calculate the sum
$sum = $var1 + $var2

# Format the output string
$output = "$var1 + $var2 = $sum"

# Output the formatted string
Write-Output $output

# Replace the variables in text with their values in the following format:

"var1" - "var2" = "sub"

# Generate random values for var1 and var2
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11

# Calculate the difference
$sub = $var1 - $var2

# Format the output string using string interpolation
$output = "$var1 - $var2 = $sub"

# Output the formatted string
Write-Output $output

'''
# Generate random starting and stopping points
$start = Get-Random -Minimum -10 -Maximum 1
$end = Get-Random -Minimum 1 -Maximum 21

# Create an array containing the range
$array = $start..$end

# Output the array
Write-Output $array
'''



















































