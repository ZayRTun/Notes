- [Home](../index.md)
---
# Data Structure
`malloc();` Allocates memory

`realloc();` Reallocates memorry passing the old pointer with its values

## DATA STRUCTURE

**`struct`** => create your own structure

__`.`__ => to access a property of an structure
	
__`*`__ => **Dereference** operator / go to that memory 

## LINKED LISTS

Creating a node structure
```C
typedef struct node
{
    int number;
    struct node *next;	//	to get the type node here cause it only registers after whole node defination we have to indicate above!!
}
node;

node *n = malloc(sizeof(node));

if (n != NULL)
{
    n->number = 2; // go to that address(->) and insert 2
    n->next = NULL; // cause the next till now is empty
                   // OR
    (*n).number = 2;	//	same as above but ugly 
    (*n).next = NULL;	//	 "	 "	  "    "   "
}
```

