- [Home](../index.md)
---
# MEMORY
**Function:** `malloc();` can be used to allocate/reserve memory in bytes.

**Function:** `free();` used to free the allocated memory so to prevent program from memory leaks.
```c
char *t = malloc(strlen(s) + 1);
free(t); // freeing t;
```
## & and *

**&** = means "Address in memory"
__*__ = means "Go to that address"

`swap(&x, &y);` calling the swap func using the "&" passing the address of the val in memory

`void swap(int *x, int *y)`  passing in arguments using the `*` go to adrress passed in call;
```c
{
	// code here
	printf("%p\n", &x);		// "%p" will print the address in memory in Hexcode.
}
```


## To define a variable that stores address must use a *

- int *number;
- char *userInput; 

**Valgrind** a debug tool for memory leaks

## Opening a file

A ".csv" file is a file that contains comma separated variables

```
fopen(); 
fclose();
```
## fgetc()
`fgetc();` Reads and returns the next character from the file pointed to.

Note: the operation of the file pointer passed in as a parameter must be "r" for read, or you will suffer an error
`char ch = fgetc(ptr1);`
```c
char ch;
while ((ch = fgetc(ptr)) != EOF) // EOR == End of file
{
    printf("%c", ch); // prints the whole file to console till EOF
}
```
## fputc()    
`fputc();` Writes or appends the specified character to the pointed-to file.

**Note:** the operation of the file pointer passed in as a parameter must be "w" for write "a" for append, or you will suffer an error.
```c
fputc(<character>, <file pointer>);
fputc("A", ptr2);

char ch;
while ((ch = fgetc(ptr)) != EOF) // EOR == End of file
{
    fputc(ch, ptr2); // get char from ptc and wrties to ptr2 till EOF
}
```

## fread()	
`fread();` Reads <qty> units of size <size> from the file pointed to and stores them in memory in a buffer (usually an array) pointed to by <buffer>

**Note:** the operation of file pointer passed in as a parameter must be 'r' for read, or you will suffer an error.
```c    
fread(<buffer>, <size>, <qty>, <file pointer>);
//Example:    
int arr[10]; // recall that arr is really just a pointer as with all arrays
fread(arr, sizeof(int), 10, ptr);
//------------
double *arr2 = malloc(sizeof(double) * 80); 	// dynamically allocating mrmory inside HEAP memory not in STACK
fread(arr2, sizeof(double), 80, ptr);
//--------------
char c;
fread(&c, sizeof(char), 1, ptr);				// note: here using a simple variable, so we need to use "&" to specify address in memory
```
## fwrite()
`fwrite();`	Writes <qty> units of size <size> to the file pointed to by reading the from a buffer (usually an array) pointed to by <buffer>.

**Note:** the operation of the file pointer passed in as a parameter must be "w" for write or "a" for append, or you will suffer an error.
```c    
fwrite(<buffer>, <size>, <qty>, <file pointer>);

int arr[10];
fwrite(arr, sizeof(int), 10, ptr);

char c;
fwrite(&c, sizeof(char), 1, ptr);

double *arr2 = malloc(sizeof(double) * 80);
fwrite(arr, sizeof(double), 80, trr);
```

## FILE
`FILE *file = fopen("phonebook.csv", "a");`  
2nd argumanet can be: 	
- "a" - for append
- "r" = for read only
- "w" = for write only
```c
fprintf(file, "%s, %s\n", name, number);	// Print (write) strings to file.

fclose(file);	// close the file.
```


