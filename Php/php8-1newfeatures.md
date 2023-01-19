**Home**
- [Home](../index.md)
---

# Php 8.1 New Features

**Array unpacking**

```php
$attributes = ['title' => 'My blog', 'body' => 'lorem ipsum'];

Post::create([
	...$attributes,
	...['category_id' => 1]
]);

```

**New never return type**

- A never-returning function must not return
```php
function visit($url): never
{
	header('Location:');

	// you can never return from this function
}
```


**Constructor initializer**

```php
interface Newsletter
{
	public function subscribe($list);
}

class MailchimpNewsletter implements Newsletter
{
	public function subscribe($list)
	{
		var_dump('testing');
	}
}

class Signup
{
	// public function perform(Newsletter $newsletter = null)
	// {
	// 	$newsletter ??= new MailchimpNewsletter();

	// 	$newsletter->subscribe('somelist');
	// }

	// instead you can now in php 8.1 can do the following
	public function perform(Newsletter $newsletter = new MailchimpNewsletter())
	{
		$newsletter->subscribe('somelist');
	}
}

(new Signup())->perform();
```


**Read only access for class properties**

```php
old school
class Project
{
	public function __construct(protected string $uid)
	{
	}

	// old school
	// using accessors
	public function getId()
	{
		return $this->uid;
	}
}
```

**Using `readonly` reduces the use of accessors**
**can only read and not change**

```php
class Project
{
	public function __construct(public readonly string $uid)
	{
	}
}

$p = new Project('sldfjsldkf');

var_dump($p->uid); // what do you do if you need to read the uid
```

## Enums

**Consider having a number of fixed options**

- Compass
  - North, South, East, West

- Coin
  - Heads, tails

```php

enum CoinFlip
{
	case Heads;
	case Tails;
}

// You can also associate values to enums
enum CoinFlip: string
{
	case Heads = 'heads';
	case Tails = 'tails';
}

function test(CoinFlip $flip)
{
	// you can get the value or the name of the enum
	// var_dump($flip->value); // -> heads
	var_dump($flip->name); // -> Heads
}

test(CoinFlip::Heads);
```

**enum methods**
```php
enum PostStatus
{
	case Draft;
	case Published;

	public function asIcon()
	{
		return match ($this) {
			self::Draft => '...',
			self::Published => '+++',
		};
	}
}

echo PostStatus::Draft->asIcon();
```