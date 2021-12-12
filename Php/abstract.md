**Home**
- [Home](../index.md)
---

# Abstract Class


## Abstract Class
1. Being an Abstract Class you remove the ability to instantiate the class directly.
2. However unlike an `interface` the class can include any behavior or functionalities that you need.
3. However it can also declare `abstract` methods, these are methods that it does not and usually can not implement directly, it needs specifics from the subclass.
4. But nonetheless it's still a requirement. If you are extending an `Abstract Class`, you have to implement required methods.

```php
<?php

// Abstract Class
abstract class AchievementType
{
    public function name()
    {
        $class = (new ReflectionClass($this))->getShortName();
        return trim( preg_replace('/[A-Z]/', ' $0', $class) );
    }

    public function icon()
    {
        return strtolower( str_replace(' ', '-', $this->name() ) ) . '.png';
    }

    abstract public function qualifier($user);
}

// Subclasses that Extends the Abstract Class
class FirstThousandPoints extends AchievementType
{
    public function qualifier($user)
    {

    }
}

// Subclasses that Extends the Abstract Class
class FirstBestAnswer extends AchievementType
{
    public function qualifier($user)
    {

    }
}

// Subclasses that Extends the Abstract Class
class ReachTop50 extends AchievementType
{
    public function qualifier($user)
    {
        // TODO: Implement qualifier() method.
    }
}

$achievement =  new ReachTop50();
$achievement->qualifier('John');
echo $achievement->name();
```