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
['Frodo', 'Sam', 'Mary', 'Pip']
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
3 good syntax for while loops
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
 12             continue
 13          elif guess < n:
 14             print("too low!!!")
 15             continue
 16 guess_number(23)
'''

inventory = {'lotr':60.0, 'poke':61, 'stepbros':19} 
  2 order = [('lotr', 4),('poke', 1)]  #these are tuples due to bracket usage 
  3 total = 0
  4 for i in order:
  5     print(i[0])
  6 order[0][0]
  7 'lotr'
  8 order [0][1]
  9 4
 10 order[0][1]*inventory[order[0][0]]
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
 


