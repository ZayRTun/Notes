- [Home](../index.md)
---
# Algorithms
- Linear Search
- Binary Search
- Bubble Sort

```python
// Sudo code
If no items
	Return false
If middle item is 50
	Return true
Else if 50 < middle item
	Search left half
Else if 50 > middle item
	Search right help
```

Linear search is in a straight line = n	n/2

logarithmic search is faster and in a curved line = log2n

## Big O notation just means on the order of.

You can say "On the order of n" = O(n)

you can say "on the order of n over 2 =	O(n/2)

you can say 'on the order of log n' = O(log n)/O(log 2 n)

### Big O notation is just meant to be proximity...

<pre>
A cheat sheet of running time or how many steps does it make....
    
O(n²)		= 	bubble sort, selection sort
O(n Log n)	= 	merge sort
O(n)		=	linear search 
O(log n)	= 	binary search
O(1)
</pre>

## Ω - Capital Greek Omega

It's the opposite of big O notation. Where Big O is essentially an upper bound on how much time an algorithm might take.

Sometimes where you lucky you can get a result on the first step which is a lower bound steps.
<pre>
Ω(n²)		=	selection sort
Ω(n log n)	= 	merge sort
Ω(n)		=	bubble sort,
Ω(log n)
Ω(1)		=	linear search (omega of 1)	/	binary search (omega of 1) 	
</pre>


Θ - Capital Theta in greek

If an algorith has a upper bound and a lower bound that are identicle, then you can describe it using a 
short hand notation Theta
<pre>
	Θ(n²)		=	selection sort
	Θ(n log n)	= 	merge sort
	Θ(n)		=	
	Θ(log n)
	Θ(1)		=	
</pre>

## CUSTOM DATA TYPES

**To define one** 
```c
typedef struct		// define type
{
    string name;	// properties
    string number;
}
person;				// name of data type	
```
**To add to an array of person**
```c
person people[2];
people[0].name = "Zay";
people[0].number = "32323232";
people[1].name = "tom";
people[1].number = "4356454";				
```		 
**SORTING**

- Bubble Sort - that bubbles up to right step by step
```c
// Sudo code
Repeat n-1 times
    For i from 0 to n-2
        if i'th and i+1'th elements out of order
            Swap them		

// Above in Big O notation is :
    (n-2) x (n-2)
    n² - 2n - 1n + 2
    n² - 3n + 2

    O(n²) 
```

- Selection Sort
```c
// Sudo Code
For i from 0 to n-2	
    Find smallest item between i'th item and last item
    Swap smallest item with i'th item

// Above in Big O notation is :
n + (n-1) +(n-2) +...+1
n(n+1)/2
(n² + n)/2
n²/2 + n/2

O(n²)
```

- Merge Sort
```c
// Sudo code
If only one item
    return
else
    sort left half of items
    sort rigt half of items
    Merge sorted halves

// Above in Big O notation is :
    O(n log n)
```





















