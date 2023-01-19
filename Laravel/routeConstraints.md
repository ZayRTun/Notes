**Home**
- [Home](../index.md)
---
# Route Wildcard Constraints

## Use the `->where()`
- First Argument is the `$slug`
- Second Argument is an regular expression `[A-z_\-]+`

```php
Route::get('/post/{post}', function ($slug) {
	// code...
})->where('post', '[A-z_\-]+');
```

## Available Helpers
- `->whereAlpha($slug) = '[a-zA-Z]+'`
- `->whereAlphaNumeric($slug) = '[a-zA-Z0-9]+'`
- `->whereNumber($slug) = '[0-9]+'`

```php
Route::get('/post/{$post}', function ($slug) {
	// code...
})->whereAlpha('post');
```
