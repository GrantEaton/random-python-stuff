# random-python-stuff
Lets learn some lessser-known, yet helpful things about Python 2! Basically this is just a place for me to store python-based stuff for later reference.

##### Should I use %s or %r for formatting?
You should use `%s` and only use `%r` for getting debugging information about something. The `%r` will give you the "raw programmer's" version of variable, also known as the "representation."

### lists
##### Sort list
``` student_tuples = [
     ('john', 'A', 15),
     ('jane', 'B', 12),
     ('dave', 'B', 10),
     ]
sorted(student_tuples, key=lambda student: student[2])   # sort by age
output: [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

##### Filter list
```>>> def f(x): return x % 3 == 0 or x % 5 == 0
...
>>> filter(f, range(2, 25))
[3, 5, 6, 9, 10, 12, 15, 18, 20, 21, 24]
```

##### Map func
```>>> def cube(x): return x*x*x
...
>>> map(cube, range(1, 11))
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```
##### Zip func
```numberList = [1, 2, 3]
strList = ['one', 'two', 'three']
```
gives
```{(1, 'one'), (3, 'three'), (2, 'two')}```

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
##### General loops
*normal:*
```>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
*pythonic*
```squares = [x**2 for x in range(10)]```

### Maps
*create a map*
```{'one': 1, 'two': 2, 'three': 3}```

*Create map with list of tuples*
```
list = [('one', 1), ('two',2), ('three',3)]
map = dict(list)
```
*or do the opposite*
`items(map)`

###### Methods
*delete key*
`del map[key]`
*check if key in map*
`key in map`
*get value from map and delete it*
pop(map)
