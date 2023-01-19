**Home**
- [Home](../index.md)
---

# Constructor properties

```php
// In the old days
// class User
// {
// 	protected $name;

// 	public function __construct($name)
// 	{
// 		$this->name = $name;
// 	}
// }

// class Plan
// {
// 	protected $name;

// 	public function __construct($name)
// 	{
// 		$this->name = $name;
// 	}
// }

// class Signup
// {
// 	protected User $user;
// 	protected Plan $plan;

// 	public function __construct(User $user, Plan $plan)
// 	{
// 		$this->user = $user;
// 		$this->plan = $plan;
// 	}
// }

// Now in PHP 8
class User
{
	public function __construct(protected $name)
	{
	}
}

class Plan
{
	// specifying arg type and default
	public function __construct(protected string $name = 'monthly')
	{
	}
}

class Signup
{

	protected Plan $plan;

	// Can also mix
	public function __construct(protected User $user, Plan $plan)
	{
		$this->plan = $plan;
	}
}

$user = new User('john_dow');
$play = new Plan('yearly');

$signup = new Signup($user, $play);


var_dump($signup);
```