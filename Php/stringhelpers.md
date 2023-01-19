**Home**
- [Home](../index.md)
---

# New String helperso

**`str_starts_with`**
```php
$id = 'inv_lskdjfsdfjlsdk';

// old school way
// $result = stripos($id, 'inv_') === 0;

// php 8 way
$result = str_starts_with($id, 'inv_');
```


**`str_ends_with`**
```php
// old school way, reverse
// $result = stripos(strrev($id), strrev('inv_')) === 0;

// php 8 way
$result = str_ends_with($id, '_inv');
```


**`str_contains`**
```php
$url = 'https://example.com?id=12';


// old school way, reverse
// $result = stripos(strrev($id), strrev('inv_')) !== false;

// php 8 way
$result = str_contains($url, '?');

var_dump($result);
```