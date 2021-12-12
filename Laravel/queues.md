**Home**
- [Home](../index.md)
---

# Laravel Queues using Redis & Laravel pRedis
```php
// Dispatching immediately
Route::get('/', function () {
    dispatch(function () {
        logger('I have to tell you about the future!');
    });

    return 'Finished';
});

Route::get('/', function () {
    dispatch(function () {
        logger('I have to tell you about the future!');
    })->delay(now()->addMinutes(2));

    return 'Finished';
});

```