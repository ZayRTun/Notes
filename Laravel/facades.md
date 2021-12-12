**Home**
- [Home](../index.md)
---

# Laravel Facades Demystified
**The request facade**  
`vendor/laravel/framework/src/Illuminate/Support/Facades/Request.php`

```php
return view('welcome');
return View::make('welcome');

// Request
return request('name');
return Request::input('name'); // identical as above

```
