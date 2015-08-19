## Just enough basic-python to poke yourself in the eye. 

#### Built-In Object Types 

For all of the below, these are simply for reference - we'll get into some of the inner 
workings of these things later. For now, I just want to introduce you to the built-in 
object types and get you a more familiar with their different representations. 

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
	yum. Dictionaries are not ordered. 

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


