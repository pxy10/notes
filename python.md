## commands

### input

python2: raw_input()
python3: input()

接收用户输入的内容, 存储为字符串

```python
y = float(raw_input('Enter a number: '))
x = raw_input('Enter your name: ')
```

### assert

assert: same as C++
`assert type(x) == int and x>=0`

add comments of a function:
```python
def func1(x, y)；
“““this function is used to...;
    input: x should be an integer; y should be a float”””
   return x + y
```

### global

全局变量, 通过global声明, 在每个使用了该变量的函数内部都需要用global声明一下

```python
def fibMetered(x):
    global numCalls
    numCalls += 1
    if x == 0 or x == 1:
        return 1
    else:
        return fibMetered(x-1) + fibMetered(x-2)


def testFib(n):
    for i in range(n+1):
        global numCalls
        numCalls = 0
        print('fib of ' + str(i) + ' = ' + str(fibMetered(i)))
        print('fib called ' + str(numCalls) + ' times')
```

### tuples

In python, tuples can be defined with `(element1, element2...)`.

```python
# create a new tuple
t1 = (1, 'two', 3)
t2 = (t1, 'four')
t3 = ('five',) # the "," is used to show that 't3' is a tuple with one single element. If not defined with ",", t3 will be treated as a string
t4 =() # the empty tuple

# To add an element or a new tuple to a existing tuple, "+" can be used.
t3 = t1 + t2
t4 = t3 + (1,)

# iterating in a tuple
sum = 0
for i in t1；
    sum += i
```

### lists

difference between lists and tuples:

+ 'tuple' object does not support item assignment, which means the elements in tuple can not be changed.

+ `list = [1, 2, 4]`, list object uses "[]" rather than "()";

+ list with one single element: `list = [3]`, donot like what we did with tuple `tuple = (3,)`

Opreation "+" can help combine two lists. `newlist = list1 + list2`

```python
# make a clone of a list
Clone = list[:] # Clone is the copy of list, once it's created, it has no relationship with "list"
SameList = list # SameList is equal to list
```

**One can use function object as the element of list or the formal parameter of a function**

```python
def applyFuns(L, x):
    for f in L:
        print(f(x))

applyFuns([abs, int, fact, fib], 4)
```

### map

`Map` applies a function to all the items in an input_list: `map(function_to_apply, list_of_inputs)`

```python
items = [1, 2, 3, 4, 5]
squared = []
for i in items:
    squared.append(i**2)
# same code with "map"
items = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, items)) # "lamda x: x**2" is a function object

#  Instead of a list of inputs we can even have a list of functions!
def multiply(x):
    return (x*x)
def add(x):
    return (x+x)

funcs = [multiply, add]
for i in range(5):
    value = list(map(lambda x: x(i), funcs))
    print(value)

# Output:
# [0, 0]
# [1, 2]
# [4, 4]
# [9, 6]
# [16, 8]

# General form: an n-ary function and n collections of arguments
L1 = [1, 28, 36]
L2 = [2, 57, 9]
map(min, L1, L2)
```

### dictionaries

syntax: `dic = {'key1': value1, 'key2': value2, ...}`

```python
monthNumber = {1: 'Jan', 2: 'Feb', 'Feb': 2, 'Jan': 1}
# insertion
monthNumer['Mar'] = 3
# iteration
listofkey = []
for key in monthNumnber: # return the key inside the dictionary
    listofkey.append(key)
# listofkey is the same as
monthNumber.keys()
```

Keys in a dictionary can not be changed, but the value can be changed. In this way, a tuple can be applied as a key, but a list cannot.


## Modules

One can group some parameters and functions into a single .py file, for example test.py. Then this file can be imported to the environment wherever you want to use the parameters or functions.
```python
import os
os.chdir("the directory of test.py")
# example1 of import
import test # import test.py, the objects inside test.py can be accessed via test.func1()

# example2 of import
from test import * # import all of the objects inside test.py, the objects can be used directly.

# example3 of import
from test import func1, func2 # import part of the objects inside test.py, the objects can be used directly.
```