**Home**
- [Home](../index.md)
---

# Caching
## `cache()->remember($name, $seconds, fn () => Post::all())`

```php
public static function find($slug)
{
	if (!file_exists($path = resource_path("posts/$slug.html"))) {
		throw new ModelNotFoundException();
	}

	return cache()->remember("posts.$slug", 1200, fn () => file_get_contents($path));
}
```