- [Home](../index.md)
---
# Introduction to C
**A standard IO library of C**
`#include <stdio.h>`

```c
int main(void) {
	printf("hello, world");	
}
```

To call the above in terminal for file name of : hello.c

`clang hello.c 
clang -o hello hello.c
./hello`

## Data Types 

**Int**
	
	int	-	can take upto + - 2 billion
	unsigned int	-	can go upto + 2 billion

**Char**

	char	-	type is used for string a single characters.
	
*character always take up 1 byte of memory (8 bits)
this means the range of value they can store is necessarily limited to 8 bits worth of information.
-128 - 0 - 127*

*Thanks to ascii we've developed a mapping of character like A,B,C etc to numeric values in the positive side of this range.*

**ASCII**
Capital A is mapped to **65**   
Lowercase a is mapped to **97**



**Float**

	float	-	data type is used for variables that will store floating-point values, also known as real numbers.

Floating points values always take up 4 bytes of memory (32bits),
its a little complicated to describe the range of float, but suffice it to say with 32bits of precision, some of which might be used for an integer	part, we are limited in how precise we can be.

**Double**

**double** data type is used for variables that will store floating-point values, also known as real numbers.
- the difference is that doubles are double precision. They always take up 8 bytes of memory (64 bits)
- with an additional 32 bits of precision relative to a float, 
	doubles allow us to specify much more precise real numbers.


`<cs50.h>` library
Included data types

-bool
-string