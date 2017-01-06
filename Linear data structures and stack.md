# Linear data structures
linear structures can be thought of as having two ends, whose items are ordered on how they are added or removed.

What distinguishes one linear structure from another is the way in which __items are added and removed__, in particular __the location where these additions and removals occur__. these variations give rise to some of the most useful data structures in computer science:


- stacks

- queues

- deques

- lists

---

# Stack

## what is a stack?

A stack is an ordered collection of items where the addition of new items and the removal of existing items always takes place at the same end. This end is commonly referred to as the __"top"__. The end opposite the top is known as the __"base"__.

In a stack, the most recently added item is the one that is in position to be removed first. This ordering principle is sometimes called __LIFO__, last-in first-out.

Examples of stacks occur in everyday situations:

- a stack of trays or plates



- a stack of books on a desk


## The reversal property of stack

Stacks are fundamentally important, as they can be used to reverse the order of items. __The order of insertion is the reverse of the order of removal__:


![The reversal property of stack](http://ww1.sinaimg.cn/mw690/0064vN5Tjw1fbfsswwlwpj30e6065gly.jpg)

Examples:

- when navigating web pages, the URLs are going on the stack

- the Python data object stack

- when running programs, the instructions are going on the stack


## The stack abstract data type

### Abstract data type (ADT)

#### What is ADT?

A logical description of how we view the data and the operations that are allowed.


#### Information hiding

The user interacts with the interface, using hte operations that have been specified by the abstract data type. The user is not concerned with the details of the implementation of the ADT:

![ADT](http://ww3.sinaimg.cn/mw690/0064vN5Tjw1fbfvditpp2j307807r3yn.jpg)


#### data structure

The implementation of an ADT, often referred to as a data structure, will require that we provide a physical view of the data using __some collection of programming constructs and primitive data types__.

There will usually be many different ways to implement an ADT.


#### The big picture

The idea of abstraction data type provides an implementation-independent view of the data. The user can remain focused on the problem-solving process without getting lost in the details.

By creating models of the problem domain, we are able to utilize a better and more efficient problem-solving process.


### The stack operations

Stacks are ordered LIFO, the operations includes:

- Stack()
- push()
- pop()
- peek()
- isEmpty()
- size()

|Stack Operation | Stack Content | Return Value |
|:---------------|---------------|--------------|
|`s.isEmpty()`   |`[]  `         |`True`        |
|`s.push(4)`     |`[4]`          |              |
|`s.push('dog')` |`[4, 'dog']`   |              |
|`s.peek()`      |`[4, 'dog']`   |`'dog'`       |
|`s.push(True)`  |`[4, 'dog', True]` |          |
|`s.size()`      |`[4, 'dog', True]` |`3`       |
|`s.isEmpty()`   |`[4, 'dog', True]` |`False`   |
|`s.push(8.4)`   |`[4, 'dog', True, 8.4]` |     |
|`s.pop()`       |`[4, 'dog', True]` |`8.4`     |
|`s.pop()`       |`[4, 'dog']`   |`True`        |
|`s.size()`      |`[4, 'dog']`   |`2`           |


## Implementing a Stack in Python

In any object-oriented programming language, the implementation of choice for an abstract data type is the creation of a new class. The operations of ADT are implemented as methods.

```python
class Stack:
"""the implementation of stack structure in python"""
    def __init__(self):
        self.items = []
    
    def push(self, item):
        self.items.append(item)
        return
        
    def pop(self):
        return self.items.pop()
    
    def peek(self):
        return self.items[-1]
    
    def isEmpty(self):
        return self.items == []
    
    def size(self):
        return len(self.items)
```


## Simple Balanced Parentheses Checker

using stacks to solve a real computer science problem that how to check whether parentheses are correctly balanced or unbalanced in programming language structrues.

```python

def is_par_balanced(str_with_par):
    s = Stack()
    
    for item in str_with_par:
        if item == '(':
            s.push(item)
        elif item == ')':
            if s.isEmpty():
                return False
            else:
                s.pop()
        else:
            pass
    
    return s.isEmpty()
```

        