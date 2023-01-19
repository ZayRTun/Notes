**Home**
- [Home](../index.md)
---

# Union types

**php 8 union lets you use multiple types** 

```php
class User
{
	// public function makeFriendsWith(User|string|DateTime $user)
	// public function makeFriendsWith(mixed $user) // mixed is like string|array|bool
	// public function makeFriendsWith(iterable $user) // iterable is like arrays|collection|traversible object
	// public function makeFriendsWith(callable $user)
	public function makeFriendsWith(mixed $user)
	{
		var_dump('Yay friends ' . is_string($user) ? $user : 'object');
	}
}


$joe = new User;
$sam = new User;

$joe->makeFriendsWith($sam);
$joe->makeFriendsWith('sam');
$joe->makeFriendsWith('next week');

```