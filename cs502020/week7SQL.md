- [Home](../index.md)
---
# SQL								
## SQL Datatypes:
- **BLOB** --	for storing BINARY data
	
- **INTEGER**
    - smallint  (< less than others)		
    - integer	(32bit)
    - bigint    (64bit)
	
- **NUMERIC**   (is more for catch all the rest of types)
  - boolean
  - date
  - datetime
  - numeric(scale, precision)	-- you can specify exactly how many digits you want befor or after the decimal.. you can be super super precise with calculations!!
  - time
  - timestamp
	
- **REAL** -- floats like in C
    - real				32bit		
    - double precision	64bit
		
- **TEXT**
    - char(n)				-- 	you can specify exactly how many characters you want is a column
    - varchar(n)			-- 	for variable number of characters, you can specify an upper bound forcharacters that can store in the column
    - text
	
## SQL SYNTAX
	
**FUNCTIONS:** `AVG, COUNT, DISTINCT, MAX, MIN, WHERE, LIKE, LIMIT, GROUP BY, ORDER BY, JOIN`

**CREATE/INSERT**
```sql
CREATE TABLE table (column type, ...);
CREATE TABLE table (column type, ...) VALUES (value, ...);
```
**SELECT**
```sql
SELECT columns FROM table;

SELECT title FROM favorites; 
--	gives u all of the title of that db

SELECT title FROM favorites LIMIT 10; 
-- will return on 10 title

SELECT DISTINCT(title) FROM favorites;	
-- will filter out all of the duplicates in title

SELECT title FROM favorites WHERE title = "The Office";
-- or	
SELECT title FROM favorites WHERE title LIKE "%Office%"; 
--	% is a placeholer. anything can go b4 & after!

-- count total number of "Office"
SELECT COUNT(title) FROM favorites WHERE title LIKE "%Office%";

SELECT columns FROM table WHERE condition:
```
**UPDATE**
```sql
UPDATE table SET column=value WHERE condition;

UPDATE favorites SET title = "The Office" WHERE title LIKE %office%; 
--	will set/update all titles thats like "office" to "The Office"
```	
**DELETE**
```sql
DELETE FROM table WHRE condition; 
--The delete statement  WARNING!!

DELETE FROM favorites WHERE title = "Friends"; 
-- 	delete record that has the title "Friends"

DELETE FROM favorites WHERE title LIKE "%friends%";	--	might delete other records with the title "friends"
```
**DROP**	
```sql
DROP TABLE favorites; 
-- will drop the whole Favorites table
```

