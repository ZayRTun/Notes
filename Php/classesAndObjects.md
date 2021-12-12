**Home**
- [Home](../index.md)
---

# Php Classes and Objects

## Here we are defining classes using regular constructor and static constructor
-   A Static Constructor for the class that's more expressive

```php
<?php

class Team
{
    protected $name;
    protected $members = [];

    public function __construct($name, $members = [])
    {
        $this->name = $name;
        $this->members = $members;
    }

    /**
     * A Static Constructor for the class
     * that's more expressive
     * @param mixed ...$params
     * @return static
     */
    public static function create(...$params)
    {
        return new static(...$params);
    }

    public function name()
    {
    }

    public function members()
    {
        return $this->members;
    }

    public function add($member)
    {
        $this->members[] = $member;
    }

    public function cancel()
    {
    }

    public function manager()
    {
    }
}
```
```php
class Member
{
    protected $name;

    public function __construct($name)
    {
        $this->name = $name;
    }

    public function lstViewed()
    {
        //
    }
}
```

## Here we instantiate an instance using the `new` keyword.
```php
$acme = new Team('Acme', [
    'John Doe',
    'Jane Doe'
]);

```
## But we can also use static constructor which helps the way you speak your code the business.
-   Here using a static constructor that is more expressive

```php
$acme = Team::create('Acme', [
    new Member('John Doe'),
    new Member('Jane Doe')
]);

var_dump($acme->members());
```