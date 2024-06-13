# Day1/0
## ssh command
This command will login to our linops as student:
`ssh student@10.x.x.x -X`

this is a whatever loop or code 
```
fruits = ["apple", "banana"}
for x in fruits:
  print(x) 
```
cybbh day 0 setup
192.168.65.20, 10.50.26.104 is the linops ip

$HOME/.vimrc

syntax enable
set tabstop=4
set shiftwidth=4
set expandtab
set number
filetype indent on
set autoindent

$HOME/.nanorc

set tabsize 4
set tabstospaces
set linenumbers

set nonumber/number to take numbered lines away

when declaring a string use single quotes '' or doub les 

capitalize true or false for booleans at the t or f

cybbh python 

single and double quotes are literal characters

to get element out of a list like 'hello world' [0] gives H

list ('hello world') makes a list 

b = list(a)

tuples cant be chnaged but overwritten and gives () when listing 

b[0] = 'j' makes h a j

splitting:
  a.split('') makes the variable a (hello world) into '[hello', 'world'] with a being "hello world"

  user:passwd gets split by the : via .split(':')

JOIN 

  a = '@'.join(b) adds a @ to every char
  does h@e@l@l@o@

hobbits = ['frodo', 'sam', 'tomcat'] #declares hobbits as an array

frodo would be index 0 sam 1 tom 2

FORMAT

  print('{] {} {} are hobbits'.format(hobbits[0],hobbits[1],hobbits[2]))

  gives the names are hobbits

  JOIN SPLIT AND FORMAT MUST LEARN 

SPLIT AN EMAIL

  '''
  email = 'name@domain.com' declares email as the string in ''

  ['name', 'domain', 'com']
  print()
  email = 'name@domain.com'
  3 part1 = email.split('@')
  4 part2 = '.'.join(part1)
  5 part3 = part2.split('.')
  6 
  7 print(part3)
  ''`


  ```
def filtewr.list(l)
  new_list =[]
  for x in l:
    if type(x) != str:
      new_list.apend(x)
  return new_list
```

MIN is a function that gives the smallest value in an array

lists can be changed, tuples cannot

USE OF APPEND
```
  >> fellowship = []
>>> fellowship.append('Frodo')
>>> fellowship
['Frodo']
>>> fellowship.append('Sam')
>>> fellowship.append('Mary')
>>> fellowship.append('Pip')
>>> fellowship
['Frodo', 'Sam', 'Mary', 'Pip']ist = each.split(readlines())
```

input() allows you to type into the function and get tat as a reult, \n gives a new line

```>> input('do sum')
do sumoh hell naw  #you need to add a space in between m and ' or a newline 
'oh hell naw'
>>> var = input('type something:\n')
type something:
1
>>> var
'1' is a string 
>>> var = input('type something:\n')
type something:
3 changed the value of var
>>> var
'3'
>>> var = int(input('type something:\n')) changed the type of the value 
type something:
1
>>> var
1
```

FLOW CONTROL/LOOPS

>> for hobbit in fellowship:
...     print(hobbit + 'is in the fellowship') hobbit is a created variable and applies to every object in the list
... 
Frodo is in the fellowship    #for loops iterate through each item, this code block goes through each name and prints whatever name is in the fellowship
Sam is in the fellowship
Mary is in the fellowship
Pip is in the fellowship
>>> 

Pass	30	30	
BRANCHING (if elif and else)
the statements end in a colon

if hobbit == 'Sam':
print(hobbit + ' is wise')

```
for hobbit in fellowship:
  4     if hobbit == 'sam':
  5         print(hobbit + ' is wise') #hobbit is a prev estsablished array
  6     elif hobbit == 'pip':
  7         print(hobbit + ' is a tool')
  8     else:
  9         print(hobbit + ' is a hobbitses')
```

num = 0
  2 while num <=5:    as lng as its less than 5 it goes and prints up 1 keep in mind num is 6 but it isnt printed because it broke the loop
  3     print(num)
  4     num += 1

BREAK AND CONTINUE 
```
while True:
  usr = input('type pass, break, or continue:\n') # gives a prompt that reads whats in the ''
  if usr == 'pass': #if they type any of these
    pass     GOES TO NEXT LINE   
    print('this is pass")
  elif usr == 'break':
    break breaks out the loop or script 
    print('this is break')
  elif usr == 'continue':
    continue doesnt got out of its block but does go back to the loop 
    print('this is continue')
  else:
    print('please choose a better option')

def digitize(n):
    num_array = [] # make empty array
    for number in str(n): # make n into string to interate through 
        num_array.insert(0, int(number)) # insert number into 1st position (reverses it)
    return num_array # return array
``` 

lst = []  #makes an empty array
lst.append('hi')   #adds hi to the end of lst
lst
['hi']

tuples are parenthesis and lists are brackets

## DAY 2
# slicing 
when start stop stepping the stop isnt cunted in a print/list
if no number is put got the list like lst[0::2} itll start at 0 stop at the max or defualt number and adds by 2

# step backwards
lst[-1::]
[10]
lst[::-1] this coutnts down from 10 to 0 # NOTE: FOR THIS ARRAY THERE ARE 11 NUMBERS 0-10


# ASCII

ord('a')
97
ord('z') #gives the positional number of an ASCII character 
122

chr(97) #gives the ASCII character for a number
'a'

# range
>>> range(10)
range(0, 10)
>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

list(range(5,10))
[5, 6, 7, 8, 9]
>>> list(range(5,11,2)) #START,STOP,STEP
[5, 7, 9]

for num in  range(2,11,2):
print(num) #prints a number in the range for each line

# length 

list(range(len(hobbits))) 
[0, 1, 2] #if theres 3 hobbits

for i in range(len(hobbits)):
  print(hobbits[i])
frodo
sam
bilbo

def two_sum(numbers, target)
  length = range(len(numbers))
  for i in length:
    for x in length:
    if x ==0:
      pass
    elif x == i:
      pass
    elif numbers[i] + numbers[x] == target:
      print(i, x)
      break
two_sum([0,1,2,3,4], 4)

# dictionaries 

romanNumerals = {'I':1, 'V':5, 'X':10, 'L':50} #declares a key with data(left to right 
romanNumerals['X'] #when called x will give 10

romanNumerals['C'] = 100 #declares new values in the dictipnary
romanNumerals['D'] = 500
romanNumerals['M'] = 1000

for key in romanNumerals: 
  print('{} = {}'.format(key, romanNumerals[key])) #when using a for loop, you must reference the dictionary (romannumerals) to use the key
  I =5
  v = 5    #sifts through the keys
  x = 10
  etc
  
'''
# good syntax for while loops
/usr/bin/env python3
  2 
  3 def guess_number(n):
  4     pass
  5     while True:
  6          guess = int(input('Choose between 0 and 100\n'))
  7          if guess == n:
  8             print("you guessed the number!")
  9             break
 10          elif guess > n:
 11             print("too high!!!")
 12             continue #continue is not needed due to input being within the loop 
 13          elif guess < n:
 14             print("too low!!!")
 15             continue
 16 guess_number(23

inventory = {'lotr':60.0, 'poke':61, 'stepbros':19} 
  2 order = [('lotr', 4),('poke', 1)]  #these are tuples due to bracket usage 
  3 total = 0
  4 for i in order: #i is for each item, the variable for things 
  5     print(i[0]) #this would print lotr and poke
  6 order[0][0] asking what the key is 
  7 'lotr'
  8 order [0][1] #asking the number of copies in the order variable 
  9 4
 10 order[0][1]*inventory[order[0][0]] # this is saying the price of the copies times the ordered copies 
 11 240.0
 12 
 13 
 14 
 15 print(inventory['lotr']) 

 for i in order:
 13     print([i[0]]*i[1]) 
 total += inventory[i[0]]*i[1]
 gives the total for order 
 312 just gives the key aka left side and the brackets around i give the value associated to those keys like 60 and 61 for lotr and poke 
 
# *args
def myfun(*args):  after seeing *args forgo the *
  2    total = 0 #total is 0 
  3    for num in args: 
  4        print(num) #prints the number
  5        total += args #at beginning total is 0 and args is 1 so its 1 
  6    print(total) #also this print is outside the for loop therefore its why the last numbewr is 15
  7 #result is 1 2 3 4 5 15 
  8 
  9 myfun(1,2,3,4,5,)

# file IO

with open("test.txt") as fp: 
pass
YOULL USE write(string)

with open("test.exe), "w") as outfile:
outfile.write('first line\n')
lines = ['second line\n', 'third line\n', 'last line\n']
outfile writelines(lines) # when catted will show the words second third and last line

with open("test.exe), "r") as outfile::

infile.read()

with open("test.exe), "r") as infile:
infile.read(5) #reads first 5 lines
infile.readlines()  #reads all the lines

print(line)rintd the lines 

COUNT EACH CHAR

num = 0
with open('travel_plans.txt') as fp: #opens a txt file as fp then counts the number of characters of the doc with len()
    num = len(fp.read())

COUNT EACH WORD

num_words = 0 
with open('emotion_words.txt') as fp:  
    for each in fp:  
        something = each.split()  #something is each word
        num_words+=len(something) len counts only the spaces so hello world is 2 

COUNT NUMBER OF LINES 

num_lines = 0
with open('school_prompt.txt') as fp:
    num_lines = len(fp.readlines()) #reads the number of lines and counted by len

FIRST 30 CHARS

beginning_chars = 0
with open('school_prompt.txt') as fp:
    beginning_chars = fp.read(30) #read reads all bytes which includes chars

    FIND THIRD WORD IN EVERY LINE 
  three = []
    with open('school_prompt.txt as fp:
      for line in fp:
        three.append(line.split()[2]) 

      FIRST WORD OF EVERY LINE
emotions = []
with open('school_prompt.txt') as fp:
  for line in fp:
    emotions.append(line.split()[0])

IF P IS IN A WORD

pwords = []
with open('school_prompt.txt') as fp:
  for line in fp:
    for word in line.split:
        print(word) 
          if 'p' in word:
          pwords.append(word)
FIGURE OUT ALSO PRACTICE QUESTIONS


 def q1(floatstr):
  4     '''
  5     TLO: 112-SCRPY002, LSA 3,4
  6     Given the floatstr, which is a comma separated string of
  7     floats, return a list with each of the floats in the 
  8     argument as elements in the list.'''
  9     return [float(x) for x in floatstr.split(',')]   the split(',' seperates with commas 
 10     pass

def q2(*args):
 14     '''
 15     TLO: 112-SCRPY006, LSA 3
 16     TLO: 112-SCRPY007, LSA 4
 17     Given the variable length argument list, return the average
 18     of all the arguments as a float
 19     '''
 20     sum = 0
 21     count = 0
 22     for n in args:
 23         sum += n
 24         count += 1
 25     return float(sum) / count
 26     pass

def q3(lst,n):
 29     '''
 30     TLO: 112-SCRPY004, LSA 3
 31     Given a list (lst) and a number of items (n), return a new 
 32     list containing the last n entries in lst.
 33     '''
 34     return lst[-n:]
 35     pass
 36 

 def q4(strng):
 38     '''
 39     TLO: 112-SCRPY004, LSA 1,2
 40     TLO: 112-SCRPY006, LSA 3
 41     Given an input string, return a list containing the ordinal numbers of 
 42     each character in the string in the order found in the input string.
 43     '''
 44     return [ord(x) for x in list(strng)] the ord(x) is saying for every value in the strng vriable 
 45     pass

def q5(strng):
 48     '''
 49     TLO: 112-SCRPY002, LSA 1,3
 50     TLO: 112-SCRPY004, LSA 2
 51     Given an input string, return a tuple with each element in the tuple
 52     containing a single word from the input string in order.
 53     '''
 54     return tuple(strng.split())
 55     pass

 def q7(filename):
 87     '''
 88     TLO: 112-SCRPY005, LSA 1
 89     Given a filename, open the file and return the length of the first line 
 90     in the file excluding the line terminator.
 91     '''
 92     with open(filename) as fp:
 93         return len(fp.readline()) - 1 
 94     pass

def q8(filename,lst):
 97     '''
 98     TLO: 112-SCRPY003, LSA 1
 99     TLO: 112-SCRPY004, LSA 1,2
100     TLO: 112-SCRPY005, LSA 1
101     Given a filename and a list, write each entry from the list to the file
102     on separate lines until a case-insensitive entry of "stop" is found in 
103     the list. If "stop" is not found in the list, write the entire list to 
104     the file on separate lines.
105     '''
106     with open(filename, 'w') as fp:
107         for item in lst:
108             if item.lower() == 'stop':
109                 break
110             fp.write('{}\n'.format(item))
111 
112     pass

def q9(miltime):
115     '''
116     TLO: 112-SCRPY003, LSA 1
117     Given the military time in the argument miltime, return a string 
118     containing the greeting of the day.
119     0300-1159 "Good Morning"
120     1200-1559 "Good Afternoon"
121     1600-2059 "Good Evening"
122     2100-0259 "Good Night"
123     '''
124     if miltime >= 300 and miltime <= 1159:
125         return "Good Morning"
126     elif miltime >= 1200 and miltime <= 1559:
127         return "Good Afternoon"
128     elif miltime >= 1600 and miltime <= 2059:
129         return "Good Evening"
130     elif miltime >= 2100 and miltime <= 259:
131         return "Good Night"
132     pass

def q10(numlist):
135     '''
136     TLO: 112-SCRPY003, LSA 1
137     TLO: 112-SCRPY004, LSA 1
138     Given the argument numlist as a list of numbers, return True if all 
139     numbers in the list are NOT negative. If any numbers in the list are
140     negative, return False.
141     '''
142     for i in numlist:
143         if i < 0:
144             return False
145     return True
146     pass

q6
Given a dictionary (catalog) whose keys are product names and values are product
prices per unit and a list of tuples (order) of product names and quantities
compute and return the total value of the order.

#CODE FOR 6
print(catalog)
print(type(catalog))
print(order)
print(type(order))
total = 0 
for i in order:
  total += catalog[i[0]]*i[1]
return total 

.startswith("insert character") shows something that starts with that character 
type() gives the type of so,ething 
once *args is seen once the * is ignored and is a basic argument 
# for <every value> in <variable>:
  <list>.append/join/
tuple() makes something a tuple
.upper, .lower() gives caps or lowers to strings 

# An empty dictionary
my_dict = {}

# A dictionary with some key-value pairs
my_dict = {
    "apple": "a fruit",
    "car": "a vehicle",
    "book": "a source of knowledge"
}

    return s.replace("!", "") # return is a function that switches something, the first is whats being replaced the second is whats replacing something 
