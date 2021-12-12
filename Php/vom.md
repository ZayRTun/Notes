**Home**
- [Home](../index.md)
---

# Value Objects & Mutability

## Value Object
### A value object is an object that is defined according to it's value or it's data rather then a particular identity.

```php
function register(string $name, int $age)
{

}
register('John Doe', 35);
```

## However we can also pass a negative number and that doesn't make any sense
```php
register('John Doe', -35);
```
## To fix the problem we can do the following:
```php
function register(string $name, int $age)
{
    if ($age < 0 || $age > 120) {
        throw new InvalidArgumentException('That makes no sense.');
    }
}

register('John Doe', 500);
```
**#**
# Value Object
## However it still doesn't feel right
- There is more to Age then just an integer
- When you run into these situations, this is an indication that it's time to extract to a `Value Object`

## Advantages to this approach
- Avoids primitive obsession - and readability
- Helps with consistency
- Immutable (object internal cannot be changes)

```php
<?php

class Age
{
    private $age;

    /**
     * Age constructor. Cannot be negative or above 120.
     * @param $age
     */
    public function __construct($age)
    {
        if ($age < 0 || $age > 120) {
            throw new InvalidArgumentException('That makes no sense.');
        }
        $this->age = $age;
    }
}

function register(string $name, Age $age)
{
}

$age = new Age(35);

register('John Doe', $age);
```

# Mutability
## Mutable Vs Imutable
- A **Mutable** object, is an object whose internal state can be changed. **It's Mutable**
- An **Imutable** object, means it's internals cannot be changed or should not be changed.

## **Mutable** example:
```php
<?php

class Age
{
    private $age;

    public function __construct($age)
    {
        if ($age < 0 || $age > 120) {
            throw new InvalidArgumentException('That makes no sense.');
        }
        $this->age = $age;
    }

    // Here we are mutating the internal state, thus Mutable
    public function increment()
    {
        $this->age += 1;
    }

    public function get()
    {
        return $this->age;
    }
}

$age = new Age(35);
$age->increment();
var_dump($age->get());
// 36%
```
## **Imutable** example:
```php
class Age
{
    private $age;

    public function __construct($age)
    {
        if ($age < 0 || $age > 120) {
            throw new InvalidArgumentException('That makes no sense.');
        }
        $this->age = $age;
    }

    // Here we are not mutating and instead return a new of the class, thus Imutable
    public function increment()
    {
        return new self($this->age + 1);
    }

    public function get()
    {
        return $this->age;
    }
}

$age = new Age(35);
// getting a brand new instance of Age
$age = $age->increment();
var_dump($age->get());
// 36%
```