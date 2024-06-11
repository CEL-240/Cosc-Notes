# Day1
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

to get element souts of a list like 'hello world' [0] gives H

list ('hello world') makes a list 

b = list(a)

tuples cant be chnaged but overwritten and gives () when listing 

b[0] = 'j' makes h a j

splitting:
  a.split('') makes the variable a (hello world) into '[hello', 'world']

  user:passwd gets split by the : via .split(':')

JOIN 

  a = '@'.join(b)
  does h@e@l@l@o@

hobbits = ['frodo', 'sam', 'tomcat']

frodo would be index 0 sam 1 tom 2

FORMAT

  print('{] {} {} are hobbits'.format(hobbits[0],hobbits[1],hobbits[2]))

  gives the names are hobbits

  JOIN SPLIT AND FORMAT MUST LEARN 

SPLIT AN EMAIL

  '''
  email = 'name@domain.com'

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
  
