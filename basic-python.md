## Just enough basic-python to poke yourself in the eye. 

#### Built-In Object Types 

For all of the below, these are simply for reference - we'll get into some of the inner 
workings of these things later. For now, I just want to introduce you to the built-in 
object types and get you more familiar with their different representations. The first thing
to note is that **everything** in python is an object. 

```
Numbers:  
	Integers: 1234 
	Floats: 3.1415
	Irrational Numbers: 3 + 4j
	Hexadecimal: 0b111 

	In addition, Python has Decimal() and Fraction() objects that allow you to 
	make Decimals and Fractions more explicit. In practice, you will almost always
	use integers and floats. 

Strings: 
	Standard: 'spam', "Bob's"
	Unicode: u'sp\xc4m'
	Binary: b'a\x01c'

	In practice, you will almost always deal with strings in standard format, where you can 
	use either single or double quotes (note that if you are going to include an apostrophe 
	in your string, you must enclose the string in double quotes). Often times strings may 
	be read in from data in unicode format, but Python typically handles the translation 
	nicely for you (if it doesn't, you can always just case it to a string by saying 
	str(u'sp\xc4m')).

Lists: 
	Hard-coded: a = [1, [2, 'three'], 4.5] 
	Using list() constructer: list(xrange(10)) 

	Note that lists can contain any number of different types of data, and can also contain 
	an arbitrary number of nested lists. Lists store references to their data by index.
	For example, a[0] = 1, and a[1] = [2, 'three']. Note that indexing starts at 0, and that 
	lists are ordered. 

Dictionaries: 
	Hard-Coded: a = {'food': 'spam', 'taste': 'yum'}
	Using dict() constructer: dict(hours=10) 

	Dictionaries come in the format of key/value pairs, where each value in the data is 
	referenced by its key. For example, a['food'] returns 'spam', and a['taste'] returns 
	'yum'. Dictionaries are not ordered. 

Tuples: 
	Hard-Coded: a = (1, 'spam', 4, 'U')
	Using tuple() constructer: tuple('spam')

	Tuples are extremely similar to lists, but are immutable (we'll get to it in a second). 
	Tuples are accessed by index. For example, a[0] = 1, a[1] = 'spam'. 

Sets: 
	Hard-Coded: {'a', 'b', 'c'}
	Using set() constructer: set('abc')

	Sets work exactly like they do in math - each value in a set must be unique (this makes 
	sets incredibly useful for comparisons, esepcially unions/intersections). If you try to 
	construct a set with 2 or more of the same value, it will keep only 1 of that given value. 
	For example set('abcccc') = {'a', 'b', 'c'}. 

Booleans: 
	True/False

	The boolean data type takes only two values - either True or False. It is important to note
	that in python, True is stored as 1 and False is stored as 0. This can be useful to remember
	in cases where you are testing equality to 0 and your test is picking up Falses (or the converse 
	of that). 
```

#### Variables 

Variables in python do not have to be declared (either as a certain type or using the keyword var), and can change types freely. In typical coding fashion, the '=' below reads as 'assigns' instead of testing for 
equality. For example, the first statement below assigns the value of -1 to a, rather than testing if a is 
equal to -1.  

```python
a = -1 # a starts off as an integer. 
a = "I'm a new type" # a is now a string
a = ["I'm", "another", "type", "now"] # a is now a list
a = ('Yet', 'Another', 'Type', '!!!') # a is now a tuple
```

#### Indexing Sequences

Any ordered sequence (i.e. a data type that assumes a positional ordering) in python can be accesed via
index. Indexing starts at 0, and continues up to the length of (object - 1). We can access either single 
indices in our object or multiple indicies at once. 

Say a is a list. a = [1, 2, 3, 4, 5]

```python
a[0] = 1 # Index the first item. 
a[4] = 5 # Index the last item. 
a[-1] = 5 # Index the last item. When we use negative indices we start from the end and index to 
		  # the front.
a[:] = [1, 2, 3, 4, 5] # Using ':' in a sequence index returns the entire sequence. 
a[:2] = [1, 2] # Returns everything from the beginning of the sequence up to but NOT INCLUDING the 
			   # element at index 2. 
a[2:] = [3, 4, 5] # Returns everything starting at the element at index 2 up to the end of the sequence. 
a[-2:] = [4, 5] # Returns everything starting from the 2nd to last element to the end of the sequence. 
```

Now say a is a string. Strings maintain a positional ordering in python, so any of the indexing statements
above will work on a string. 

a = 'python'

```python
a[0] = 'p'
a[4] = 'o'
a[-1] = 'n'
a[:] = 'python'
a[:2] = 'py'
a[2:] = 'thon'
a[-2:] = 'on'
```

#### Indexing Dictionaries

Python dictionaries are completely different from sequences, and are known as _mappings_. Mappings store objects by _key_ instead of by relative position (i.e. what sequences do). That means that to access an object within a dictionary, we must access it by the key associated with it. This also means that each key in a dictionary must be unique. If you try to construct a dictionary with a repeated key using the dict() constructer, it will give you an error. If you try to use the hard-coded method and repeat a key, the dictionary will simply hold the last value that you assigned to the key. For example: 

```
dict(hold=10, hold=10) = ERROR ERROR!
{'hold': 10, 'hold': 12} = {'hold': 12}
```

Like previously mentioned, we access dictionaries by key, and the dictionary's values can hold entire objects. 

Say a is a dictionary: a = {'list1': [1, 2, 3, 4, 5], 'tuple1': (1, 2, 3, 4, 5), 'val': 5}

```
a['list1'] = [1, 2, 3, 4, 5]
a['list1'][2] = 3
a['tuple1'] = (1, 2, 3, 4, 5)
a['tuple1'][4] = 5
a['val'] = 5
``` 

#### Immutability

Certain objects in python are immutable, meaning that you can't change their values in place. In 
terms of the built-in object types above, numbers, strings, and tuples are immutable, whereas 
lists, dictionaries, and sets are not (i.e. they're mutable). 

What does this mean?? I've never run into immutability issues with numbers, but let's look at some of the other
data types. In practice, I don't run into immutability issues often, but immutability can be a great property 
to be able to use when you need to gaurentee that an objects' values can't change at any time during your 
program. With mutable objects, their values can be changed at any time and any place, whether you expect it 
or not. 

```
a = 'String'
a[2] = 'p' # ERROR ERROR! You can't change a string in place. 
a = 'Bozo' # I can assign a different string to the variable a, but I can't change a part of a in place. 

b = ['l', 'i', 's', 't'] # b is a list. 
b[0] = 'p' # I can change b in place. b now equals ['p', 'i', 's', 't']
```

