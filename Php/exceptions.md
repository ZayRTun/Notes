**Home**
- [Home](../index.md)
---

# Exceptions

If at any point your code encounters some abnormal situation that it doesn't know how to handle, you should throw an `Exception`.

And if it helps think very literrally, it's a way for your code to say, "Hold up, I take `exception` with what your trying to do. And I'll bubble up this exception to my superiors until somebody takes care of it.


## Genaric Exception
```php
throw new Exception('Please provide a float.');
```
### Example
```php
<?php

function add($one, $two)
{
    if (! is_float($one) || ! is_float($two)) {
        throw new Exception('Please provide a float.');
    }
    return $one + $two;
}

// ## Handling the Exception
// ## If not handled will throw an error
try {
    echo add(2, []);
} catch (Exception $exception) {
    // Many ways to handle this here
    // You can redirect the user or something else
    echo $exception->getMessage();
}
```
## `InvalidArgumentException`
We can use the above `Exception` but it's very generic an says nothing about what it's for.
Instead we can use `InvalidArgumentException` for the above case like so:
- You can also be more specific when catching the exception
```php
if (! is_float($one) || ! is_float($two)) {
    // Note, how expressive this Exception is.
    throw new InvalidArgumentException('Please provide a float.');
}
```

## Handling the `InvalidArgumentException`
- Here we are catching a **specific** exception
```php
try {
    echo add(2, []);
} catch (InvalidArgumentException $exception) {
    echo $exception->getMessage();
}
```

## Using a custom, a very specific Exception with hard coded `$message`
```php
<?php

class MaximumMembersReached extends Exception
{
    protected $message = 'Sorry, you can\'t add anymore member to this team.';
}
```

```php
<?php

class Member
{
    public $name;

    public function __construct($name)
    {
        $this->name = $name;
    }
}

class Team
{
    protected $members = [];

    public function add(Member $member)
    {
        if (count($this->members) === 3) {
            throw new MaximumMembersReached;
        }
        $this->members[] = $member;
    }

    public function members()
    {
        return $this->members;
    }
}

class TeamMembersController
{
    public function store()
    {
        $team = new Team;

        try {
            $team->add(new Member('John Doe'));
            $team->add(new Member('Jane Doe'));
            $team->add(new Member('Frank Doe'));
            $team->add(new Member('Susan Doe'));

            var_dump($team->members());
        } catch (MaximumMembersReached $e) {
            var_dump($e->getMessage());
        }
    }
}

(new TeamMembersController())->store();
```

## Using a custom, less specific Exception with hard coded `$messages`

```php
<?php

class TeamException extends Exception
{
    public static function fromTooManyMembers()
    {
        return new static('You may not add more than 3 team members.');
    }

    public static function fromTooFewMembers()
    {
        return new static('Too few members');
    }
}
```

```php
<?php

class Member
{
    public $name;

    public function __construct($name)
    {
        $this->name = $name;
    }
}

class Team
{
    protected $members = [];

    public function add(Member $member)
    {
        if (count($this->members) === 3) {
            throw TeamException::fromTooManyMembers();
        }
        $this->members[] = $member;
    }

    public function members()
    {
        return $this->members;
    }
}

class TeamMembersController
{
    public function store()
    {
        $team = new Team;

        try {
            $team->add(new Member('John Doe'));
            $team->add(new Member('Jane Doe'));
            $team->add(new Member('Frank Doe'));
            $team->add(new Member('Susan Doe'));

            var_dump($team->members());
        } catch (TeamException $e) {
            var_dump($e->getMessage());
        }
    }
}

(new TeamMembersController())->store();
```
