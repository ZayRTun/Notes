**Home**
- [Home](../index.md)
---


# Weak maps
**A week map is a key => value store**  
**keys are objects**
```php
// A week map is a key => value store
// keys are objects

// using weak map, if you unset it it will be removed

$obj = new stdClass();

$store = new WeakMap();

$store[$obj] = 'foobar';

var_dump($store);

// using weak map, if you unset it it will be removed
unset($obj);

var_dump($store);
```