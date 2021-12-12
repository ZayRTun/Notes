- [Home](../index.md)
---
# Python														
## DATA TYPES		
- bool
- float
- int
- str					
- range 	=	sequence of numbers
- list	=	sequence of mutable values
- tuple	= 	sequence of immutable values
- dict	=	collection of key/value pairs // pythons implemention of an Hash Table of C
- set		=	collection of unique values			


## REGULAR EXPRESSIONS
`import re` => Regular expression library

- . =	ANY CHARACTER
- .* =	0 OR MORE CHARACTERS
- .+ = 	1 OR MORE CHARACTERS
- ? =	OPTIONAL
- ^	= 	START OF INPUT
- $	=	END OF INPUT 

## Import statement
`from PIL import Image, ImageFilter`
```python
before = Image.open("bridge.bmp")
after = before.filter(ImageFilter.BLUR)
after.save("out.bmp")
```
---
## Pset5 in Python
```python
words = set()

// to define a function
def check(word):
	if word.lower() in words:
		return True
	else:
		return False

def load(dictionary):
	file = open(dictionary, "r")
	for line in file:
		words.add(line.rstrip("\n") # striping off the next line 
	file.close()
	return true


def size():
	return len(words)
	
def unload():
	return True	// Python doesn't require you to free memory 


```
---
```python	
s = get_string("Do you agree?\n")

if s in ["y", "Y", "yes", "Yes"]:   # you can check condition like this
    print("Aggreed")
elif s in ["n", "N", "no", "No"]:
    print("Disagreed")	
    
    
def main():	**************** using main 
    n = get_positive_integer()

    print("Finally a positive int")


def get_positive_integer():
    while True:                 # python do while loop
        n = get_int("Positive Int: ")
        if n > 0:
            break
    return n


main() 
```	
	
***************************
## Command line arguments
`from sys import argv`  # uses the sys library
```python
for i in range(len(argv)):
    print(argv[i])
```
	