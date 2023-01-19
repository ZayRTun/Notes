**Home**
- [Home](../index.md)
---

# Null Safe Operator `?`

`$user->profile()?->employment();`

```php
class User
{
	public function profile()
	{
		return new Profile;
	}
}

class Profile
{
	public function employment()
	{
		return 'Web developer';
	}
}

$user = new User;

// ---- Before php 8
// $profile = $user->profile();

// if ($profile) {
// 	echo $profile->employment();
// }

// echo $user->profile()?->employment();

// You can also chain on a Null coallascent operator ??
echo $user->profile()?->employment() ?? 'Not provided';
```