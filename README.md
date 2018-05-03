# random-python-stuff
Lets learn some lessser-known, yet helpful things about Python 2! Basically this is just a place for me to store python-based stuff for later reference.

##### Should I use %s or %r for formatting?
You should use `%s` and only use `%r` for getting debugging information about something. The `%r` will give you the "raw programmer's" version of variable, also known as the "representation."

### lists
##### Sort list
``` 
student_tuples = [
     ('john', 'A', 15),
     ('jane', 'B', 12),
     ('dave', 'B', 10),
     ]
sorted(student_tuples, key=lambda student: student[2])   # sort by age
output: [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

##### Filter list
```
>>> def f(x): return x % 3 == 0 or x % 5 == 0
...
>>> filter(f, range(2, 25))
[3, 5, 6, 9, 10, 12, 15, 18, 20, 21, 24]
```

##### Map func
```
>>> def cube(x): return x*x*x
...
>>> map(cube, range(1, 11))
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

##### Reduce 
```
>>> def add(x,y): return x+y
...
>>> reduce(add, range(1, 11))
55
```
##### Zip func
```
numberList = [1, 2, 3]
strList = ['one', 'two', 'three']
```
gives
```{(1, 'one'), (3, 'three'), (2, 'two')}```

### Strings
##### Access elements & random funcs

| operation     | result                                  |
|---------------|-----------------------------------------|
| str[i:j]      | slice of s from i to j                  |
| str[i:j:k]    | slice of s from i to j with step k      |
| str.index(x)  | index of the first occurrence of x in s |
| str.count(x)  | total number of occurrences of x in s   |

###### join (adds a delimeter)
```
str = "-"
list = ['a', 'b', 'c']
print str.join(list)
```
prints `a-b-c`

### Queue
```>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```

### Pythonic Stuff
##### List Comprehension
**normal:**
```
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
**pythonic**
```squares = [x**2 for x in range(10)]```

**with if clause**
```
>>> l = []
>>> for x in vec:
...      if x >= 0:
...           l.append(x)
```

**pythonic**
```
>>> [x for x in vec if x >= 0]
[0, 2, 4]
```
### Maps
**create a map**
`{'one': 1, 'two': 2, 'three': 3}`

**Create map with list of tuples**
```
list = [('one', 1), ('two',2), ('three',3)]
map = dict(list)
```
**or do the opposite**
`map.items()`

###### Methods
**delete key**<br />
`del map[key]`

**check if key in map**<br />
`key in map`

**get value from map and delete it**<br />
`pop(map)`

**get values/keys of map**<br />
```
map.viewkeys()
map.viewvalues()
```
**or both at the same time...**
```
for key, val in map.iteritems():
      print k, v
```

### Classes

```
class Node(object):

    left, right, val;
    
    def __init__(self, left right): 
        self.left = left;
        self.right = right;
    
```
