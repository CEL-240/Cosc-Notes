## day 1 
# login: xfreerdp /u:student /v:10.50.23.80 -dynamic-resolution +glyph-cache +clipboard
# run powershell ISE 
hit f8 for running a line and f for the whole script 
Get-Process | Format-list #processess and formats into a list 
get-help <whatever youu need help w> -Examples or -Detailed, #'s are comments, <> allow multiline comments 
measure-object # counts 
# variables
Display the start time of the earliest and latest running processes
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
Get-Process | -Name s* # c next to name for case sens

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
New-Alias -Name gh -Value Get-Help / set-alias gh get-help
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

# Create an array containing a range with a random starting and stopping point. The starting point will be a random number from -10 through 0. The ending point will be a random number from 1 through 20.
'''
# Generate random starting and stopping points
$start = Get-Random -Minimum -10 -Maximum 1
$end = Get-Random -Minimum 1 -Maximum 21

# Create an array containing the range
$array = $start..$end

# Output the array
Write-Output $array
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

# Create a variable that contains the contents of the array in reverse

Using the above example, your reversed array will be 2, 1, 0, -1, -2, -3


# Generate random starting and stopping points
$start = Get-Random -Minimum -10 -Maximum 1
$end = Get-Random -Minimum 1 -Maximum 21

# Create an array containing the range
$array = $start..$end

# Initialize an empty array to store the reversed elements
$reversedArray = @()

# Iterate over the original array from end to start
for ($i = $array.Length - 1; $i -ge 0; $i--) {
    $reversedArray += $array[$i]
}

# Output the reversed array
Write-Output $reversedArray
## IF NO REVERSE METHOD 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''----------------------------------------------------------------------------
update-help updates the help system 
get-help *processes* 
output is for the pipeline and write host is for the terminal

get-command -Noun *variable*
` (backtic) is the escape character
# range
done with ..

properties have no () like .length but getype() is a method 

##  day 2

# pipeline
get-process | get-member -membertype properties
                                      methods 

get-service | format-table name, status 

get-service | where-object -property status -eq stopped #finds stopped processes can be combined with the line 188 pipe to format it with just names but only stopped processes 

# super srrays/ hash table 

$a = @{} 
$a.getype()

get-childitem 
$cols = @{label="kb"; expression = { [int]($_.length/1kb)}}
get-childitem | format-table name, $cols 

function write-output-head {...}
write-output-host "coors light"
write-output-host "coors banquet"
write-output-host "old 4-loko"
write-output-host "yeungling"
}

write-host-head | sort gives just the 4 beers but host doesnt paasss and sort thjrough the pipline 
write-output-head | sort has the function  go through the pipes 
1..5 | sort-object 

## hash excersise 
$employee1 = [ordered]@{}
$employee2 = @{}
employee1.first = "mary"
employee1["last"] = "hopper"
employee1.ID = "001"
employee1["Job"] = "software dev"
----------------------------------------------------------------------

# Display the start time of the earliest and latest running processes

# Get all running processes
$processes = Get-Process | Where-Object { $_.StartTime -ne $null } | Sort-Object StartTime
measure-object and select object are good to know 
# Get the earliest and latest start time
$earliestStartTime = $processes[0].StartTime
$latestStartTime = $processes[-1].StartTime

# Display the start times
Write-Output "Earliest start time: $earliestStartTime"
Write-Output "Latest start time: $latestStartTime"

--------------------------------------------------------------------------

# Identify a cmdlet that returns the current date and time then using this cmdlet and Select-object, display only the current day of the week

# Get the current date and time
$currentDateTime = Get-Date

# Display only the current day of the week
$currentDayOfWeek = $currentDateTime | Select-Object -ExpandProperty DayOfWeek

# Output the current day of the week
Write-Output "Current day of the week: $currentDayOfWeek"

-----------------------------------------------------------------------------------------

# Identify a cmdlet that displays a list of installed hotfixes.

get-hotfix 

----------------------------------------------------------------------------------------

# Extend the expression to sort the list by install date, and display only the install date and hotfix ID.

# Get and sort hotfixes by install date, display install date and hotfix ID
Get-HotFix | Sort-Object InstalledOn | Select-Object InstalledOn, HotFixID

----------------------------------------------------------------------------------------

# Extend the expression further, but this time sort by description, include description, hotfix ID, and install Date.

# Get and sort hotfixes by install date, display install date and hotfix ID
Get-HotFix | Sort-Object InstalledOn, Description | Select-Object InstalledOn, HotFixID, Description

----------------------------------------------------------------------------------------

# Create a custom object that contains information about the host system using the following:

Win32_ComputerSystem

Win32_BIOS

Win32_OperatingSystem

Win32_LogicalDisk


# Retrieve information from Win32_ComputerSystem
$computerSystem = Get-WmiObject -Class Win32_ComputerSystem
$computerName = $computerSystem.Name
$manufacturer = $computerSystem.Manufacturer
$model = $computerSystem.Model
$totalPhysicalMemory = [math]::round($computerSystem.TotalPhysicalMemory / 1GB, 2)  # Convert to GB and round to 2 decimal places

# Retrieve information from Win32_BIOS
$bios = Get-WmiObject -Class Win32_BIOS
$biosVersion = $bios.SMBIOSBIOSVersion
$biosManufacturer = $bios.Manufacturer

# Retrieve information from Win32_OperatingSystem
$operatingSystem = Get-WmiObject -Class Win32_OperatingSystem
$osName = $operatingSystem.Caption
$osVersion = $operatingSystem.Version
$osArchitecture = $operatingSystem.OSArchitecture
$installedDate = $operatingSystem.InstallDate

# Retrieve information from Win32_LogicalDisk
$logicalDisks = Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3"  # DriveType 3 corresponds to local disks
$diskInfo = $logicalDisks | Select-Object DeviceID, VolumeName, @{Name="FreeSpace(GB)"; Expression={[math]::round($_.FreeSpace / 1GB, 2)}}, @{Name="Size(GB)"; Expression={[math]::round($_.Size / 1GB, 2)}}

# Create a custom object with gathered information
$systemInfo = [PSCustomObject]@{
    ComputerName = $computerName
    Manufacturer = $manufacturer
    Model = $model
    TotalPhysicalMemory_GB = $totalPhysicalMemory
    BIOSVersion = $biosVersion
    BIOSManufacturer = $biosManufacturer
    OSName = $osName
    OSVersion = $osVersion
    OSArchitecture = $osArchitecture
    InstalledDate = $installedDate
    LogicalDisks = $diskInfo
}

# Output the custom object
$systemInfo

-----------------------------------------------------------------------------------------------------------------

# Find and extract the model number from the provided lines of text. If there isn’t a model number then display to the user that a model number wasn’t found

 # Check both lines for model numbers and report individually the line and model number if found.

# Define the lines of text
$line1 = "Do you have model number: MT5437 for john.doe@sharklasers.com?"
$line2 = "What model number for john.doe@sharklasers.com?"

# Define a function to extract the model number using regex
function Extract-ModelNumber {
    param (
        [string]$line
    )
    # Regular expression to match the model number format
    $regex = "model number:\s*(\w+)"
    if ($line -match $regex) {
        return $matches[1]
    }
    return $null
}

# Extract model numbers from each line
$modelNumber1 = Extract-ModelNumber -line $line1
$modelNumber2 = Extract-ModelNumber -line $line2

# Check and report the results
if ($modelNumber1) {
    Write-Output "Line 1: Model number found: $modelNumber1"
} else {
    Write-Output "Line 1: Model number not found"
}

if ($modelNumber2) {
    Write-Output "Line 2: Model number found: $modelNumber2"
} else {
    Write-Output "Line 2: Model number not found"
}

-----------------------------------------------------------------------------------------------------------------------------------

# Part 1

Use an array to iterate and open the following

Notepad

MS Edge

MSpaint

Query the processes

Kill the processes from PowerShell

# Define the list of applications to open
$apps = @(
    "notepad.exe",
    "mspaint.exe",
    "msedge.exe"
)

# Function to start the applications
function Start-Applications {
    param (
        [string[]]$appList
    )
    foreach ($app in $appList) {
        Start-Process $app
        Start-Sleep -Seconds 1  # Give some time for the process to start
    }
}

# Function to query and return the processes by name
function Get-AppProcesses {
    param (
        [string[]]$appList
    )
    $processes = @()
    foreach ($app in $appList) {
        $processes += Get-Process -Name ($app -replace ".exe", "") -ErrorAction SilentlyContinue
    }
    return $processes
}

# Function to save Process IDs to a file
function Save-ProcessIds {
    param (
        [System.Diagnostics.Process[]]$processList,
        [string]$filePath
    )
    $processList | ForEach-Object { $_.Id } | Out-File -FilePath $filePath -Force
}

# Function to kill processes from a file
function Kill-ProcessesFromFile {
    param (
        [string]$filePath
    )
    $pids = Get-Content -Path $filePath
    foreach ($pid in $pids) {
        try {
            Stop-Process -Id $pid -Force -ErrorAction Stop
            Write-Output "Process $pid terminated successfully."
        } catch {
            Write-Output "Failed to terminate process $pid: $_"
        }
    }
}

# Start the applications
Start-Applications -appList $apps

# Give some time for the applications to start
Start-Sleep -Seconds 5

# Query the processes
$processes = Get-AppProcesses -appList $apps

# Output the processes found
Write-Output "Processes to be terminated:"
$processes | Format-Table -Property Id, ProcessName

# Save Process IDs to a file
$procFilePath = "$env:USERPROFILE\procs.txt"
Save-ProcessIds -processList $processes -filePath $procFilePath

Write-Output "Process IDs have been saved to $procFilePath."

# Kill processes from the file
Write-Output "Terminating processes from $procFilePath..."
Kill-ProcessesFromFile -filePath $procFilePath

Write-Output "Processes have been terminated."


--------------------------------------------------------------------------------------------------

# Query the processes and display only the following information in order by process ID

Process ID

Process Name

The time the process started

The amount of time the process has spent on the processor

The amount of memory assigned to the process

# Define the list of applications to open
$apps = @(
    "notepad.exe",
    "mspaint.exe",
    "msedge.exe"  # Ensure Edge is installed and available in the system path
)

# Function to start the applications
function Start-Applications {
    param (
        [string[]]$appList
    )
    foreach ($app in $appList) {
        Start-Process $app
    }
}

# Function to query and return the process information
function Get-AppProcessesInfo {
    param (
        [string[]]$appList
    )
    $processInfo = @()
    foreach ($app in $appList) {
        $processes = Get-Process -Name ($app -replace ".exe", "")
        foreach ($process in $processes) {
            $info = [PSCustomObject]@{
                ProcessID   = $process.Id
                ProcessName = $process.ProcessName
                StartTime   = $process.StartTime
                CPUTime     = $process.TotalProcessorTime
                MemoryUsage = $process.WorkingSet64
            }
            $processInfo += $info
        }
    }
    return $processInfo
}

# Start the applications
Start-Applications -appList $apps

# Give some time for the applications to start
Start-Sleep -Seconds 5

# Query the process information
$processInfo = Get-AppProcessesInfo -appList $apps

# Sort the process information by Process ID
$sortedProcessInfo = $processInfo | Sort-Object -Property ProcessID

# Output the process information
$sortedProcessInfo | Format-Table -Property ProcessID, ProcessName, StartTime, CPUTime, MemoryUsage

# Save the process information to a text file
$sortedProcessInfo | Out-File -FilePath "procs.txt"

# Read the process information from the text file
$savedProcessInfo = Get-Content -Path "procs.txt" | Out-String

# Output the process information from the text file
Write-Output $savedProcessInfo

-----------------------------------------------------------------------------------------------------------------------

# ge the ordinal date  and current date 

function Get-OrdinalDate {
    # Get the current date
    $currentDate = Get-Date

    # Get the ordinal date (day of the year)
    $ordinalDate = $currentDate.DayOfYear

    # Return the ordinal date
    return $ordinalDate
}

# Call the function and output the result
$ordinalDate = Get-OrdinalDate
Write-Output "The ordinal date of today is: $ordinalDate"

-------------------------------------------------------------------------------------------------------------------

# Create a function that takes a number(n) as an argument and returns the square(n^2) of the number. 

function Get-Square {
    param (
        [int]$n
    )

    # Calculate the square of the number
    $square = $n * $n

    # Return the square
    return $square
}

# Example usage
$n = 5
$square = Get-Square -n $n
Write-Output "The square of $n is: $square"

----------------------------------------------------------------------------------------------------------

# Create a function that takes three (3) arguments and returns the product of the arguments.

function Get-Product {
    param (
        [int]$a,
        [int]$b,
        [int]$c
    )

    # Calculate the product of the three numbers
    $product = $a * $b * $c

    # Return the product
    return $product
}

# Example usage
$a = 2
$b = 3
$c = 4
$product = Get-Product -a $a -b $b -c $c
Write-Output "The product of $a, $b, and $c is: $product"

-----------------------------------------------------------------------------------------------------------------

# Create a function that takes two(2) integer values, $a and $b, that are the lengths of two(2) legs of a right triangle and returns the length of the hypotenuse

function Get-Hypotenuse {
    param (
        [int]$a,
        [int]$b
    )

    # Calculate the square of the hypotenuse
    $cSquare = [math]::Pow($a, 2) + [math]::Pow($b, 2)

    # Calculate the length of the hypotenuse
    $hypotenuse = [math]::Sqrt($cSquare)

    # Return the length of the hypotenuse
    return $hypotenuse
}

# Example usage
$a = 3
$b = 4
$hypotenuse = Get-Hypotenuse -a $a -b $b
Write-Output "The length of the hypotenuse for legs $a and $b is: $hypotenuse"

--------------------------------------------------------------------------------------------------------------------------------------

# Create a function that takes two(2) values, $a and $b, as two(2) angles in degrees of a triangle. Return the value of the missing angle.

function Get-MissingAngle {
    param (
        [float]$a,
        [float]$b
    )

    # Calculate the missing angle
    $missingAngle = 180 - ($a + $b)

    # Return the missing angle
    return $missingAngle
}

# Example usage
$a = 60
$b = 80
$missingAngle = Get-MissingAngle -a $a -b $b
Write-Output "The missing angle for angles $a and $b is: $missingAngle"

----------------------------------------------------------------------------------------------------

# and returns the information in a hash table using the keys: first, last, age, and weight with the weight value converted to kilograms(kg) rounded to the nearest whole number

function Get-UserInfo {
    param (
        [string]$first,
        [string]$last,
        [int]$age,
        [float]$weight
    )

    # Convert weight from pounds to kilograms and round to the nearest whole number
    $weightInKg = [math]::Round($weight * 0.45359237)

    # Create a hash table with the user information
    $userInfo = @{
        first  = $first
        last   = $last
        age    = $age
        weight = $weightInKg
    }

    # Return the hash table
    return $userInfo
}

# Example usage
$firstName = "John"
$lastName = "Doe"
$age = 30
$weightInPounds = 180
$userInfo = Get-UserInfo -first $firstName -last $lastName -age $age -weight $weightInPounds
Write-Output $userInfo

----------------------------------------------------------------------------------------------------
# script block 
$myblock = { get-service | format-table name, status }

invoke-command $myblock
&$myblock

$a = @()
$b = {1+1}

$a += &$b #& is invoking b
----------------------------------------------------------------------------------------------------
get-process | group-object {$_.name.substring(0,1).toupper()} | foreach-object
{($_.name) + " "} * 7; "=============="; $_.group}
#groups by firs letter of process name and makes the group uppercase 
# fore each obj

---------------------------------------------------------------------------------------------------------

get-process | sort-object starttime | select-object -first 10 | ft processname, starttime
| select-object -expandproperty name 

-------------------------------------------------------------------------------------------------------

# comparison operators 
1..5 -eq 2 returns what is true out of the range 
"abc" -eq "abc" double quotes are used for strings 
# i is case insense and cis case sense, -ieq or -ceq

-------------------------------------------------------------------------------------

# like
"powershell", "server" -like(or -notlike) "*shell"

$txt = 'here is the model: MO354'
$pattern = 'MO(\d{3})'
$txt -match $pattern

$matches[0] gives the model number btu 1 would give numbers also -match uses REGEX PATTERNS

---------------------------------------------------------------------------------------------------------

# contains

$beer = 'spotted cow', 'left handed brewery', "knee deep", "coors light" 
$beer -ccontains "coors light"#second c on case is for case sense
---------------------------------------------------------------------------------------------------

# Create an advanced function using Begin, Process, and End, that takes two(2) arguments. The first argument being an array of at least ten(10) integers and the second argument being a single integer. Search the array argument for every occurrence of the single integer argument then return the sum of all elements in the array excluding every occurrence of the single integer argument.



function SumExcludingOccurrences {
    param (
        [int[]]$array,
        [int]$excludeInteger
    )

    $sum = 0
    foreach ($num in $array) {
        if ($num -ne $excludeInteger) {
            $sum += $num
        }
    }

    return $sum
}

# Example usage
$array = 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
$excludeInteger = 5
$result = SumExcludingOccurrences -array $array -excludeInteger $excludeInteger
Write-Output "Sum of array excluding occurrences of $excludeInteger is: $result"

----------------------------------------------------------------------------------------------------

# Create an advanced function using Begin, Process, End, that prompts the user to enter the names of three(3) U.S. States then returns the names of the states in the order of longest name to shortest name and the amount of characters in each name. make it seem like a beginner wrote it

function Get-StateNames {
    [CmdletBinding()]
    param ()

    Begin {
        Write-Output "Enter the names of three US states:"
        $stateNames = @()
    }

    Process {
        for ($i = 1; $i -le 3; $i++) {
            $stateName = Read-Host "Enter State $i:"
            $stateNames += $stateName
        }
    }

    End {
        $sortedStates = $stateNames | Sort-Object { $_.Length } -Descending
        $stateLengths = $sortedStates | ForEach-Object { $_.Length }

        Write-Output "States sorted from longest to shortest:"
        for ($j = 0; $j -lt $sortedStates.Count; $j++) {
            Write-Output "$($sortedStates[$j]) - $($stateLengths[$j]) characters"
        }
    }
}

# Call the function
Get-StateNames

--------------------------------------------------------------------------------------------------------------------------------------------------

# Create a function that extracts your current IP, Subnet and Gateway and outputs them in the following format:

Example
PS> Get-netinfo
IP: 192.168.0.1
Subnet: 255.255.255.0
Gateway: 192.168.1.1

function Get-NetInfo {
    # Retrieve network configuration
    $networkConfig = Get-NetIPConfiguration | Where-Object { $_.IPv4DefaultGateway -ne $null }

    # Extract IP, Subnet, and Gateway
    $ip = $networkConfig.IPv4Address.IPAddress
    $subnet = $networkConfig.IPv4SubnetMask.IPAddress
    $gateway = $networkConfig.IPv4DefaultGateway.NextHop

    # Output in desired format
    Write-Output "IP: $ip"
    Write-Output "Subnet: $subnet"
    Write-Output "Gateway: $gateway"
}

# Call the function
Get-NetInfo

--------------------------------------------------------------------------------------------------------------------------------------

# Create a function that extracts all the URLs found in the file "dns.txt" and outputs URLs, the amount of times the URL is found in the file and the total amount of URLs found.

function Get-URLStats {
    param (
        [string]$filePath = "dns.txt"
    )

    # Read content of the file
    try {
        $content = Get-Content -Path $filePath -ErrorAction Stop
    } catch {
        Write-Output "Error reading file: $_"
        return
    }

    # Define regex pattern to match URLs
    $urlPattern = '(?i)\b(?:https?|ftp|file)://\S+'

    # Find all URLs in the content
    $urls = $content -split '\s' | Where-Object { $_ -match $urlPattern }

    # Count occurrences of each URL
    $urlCounts = $urls | Group-Object | Sort-Object -Property Count -Descending

    # Output URLs, their counts, and total amount of URLs found
    Write-Output "URLs found in $filePath:"
    foreach ($url in $urlCounts) {
        Write-Output "$($url.Name) - Count: $($url.Count)"
    }
    Write-Output "Total unique URLs found: $($urlCounts.Count)"
}

# Example usage
Get-URLStats -filePath "dns.txt"

---------------------------------------------------------------------------------------------------------------------------

\
# for each loops 
$array = 1..5
$sum = 0
foreach ($item in $array){
    $sum += $item 
}

--------------------------------------------------------------------------------------------------------------

# while loops 
$sum = 0
whille($sum -lt 15) {
    $sum
    $sum += 1
}

$beer = ''
while($beer -ne 'coors') {
    $beers = read-host -prompt "what is the best beer?"
}

$num = 100
do { 
    $num 
    $num += 1
}while($num -lt 3)

$num = 0
do {
    $num
    $num += 1
}until($num -gt 3)


----------------------------------------------------------------------------------------------------------------------------

# for loop 
for ($num = 1; $num -le 3; $num ++)
{
    $num
}

-------------------------------------------------------------------------------------------------
# file manipulation 
allows to write to a file 
set-content -path .\example.txt -value 'drink water' 
add-content -path .\example.txt -value "gatorade is better"
get-content .\example.txt 

-------------------------------------------------------------------------------------------------


















































