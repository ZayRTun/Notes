**Home**
- [Home](../index.md)
---

## Service Container

**A service container is a Container for Services !**
**It's a place to `store` and `retrive` services**

Service is catch all term, it can be anything like a string, a collection, object, ...

```php
namespace App;

class Container
{
    protected $bindings = [];

    public function bind($key, $val)
    {
        $this->bindings[$key] = $val;
    }

    public function resolve($key)
    {
        if (isset($this->bindings[$key])) {
            return call_user_func($this->bindings[$key]);
        }
    }
}

// And you web route
Route::get('/', function () {
    $container = new App\Container();

    $container->bind('example', function () {
        return new \App\Example();
    });

    $example = $container->resolve('example');

    ddd($example);
});
```

The ides is that you bind something to container and then you resolve from it when you need it...
___

# Laravel Container

`app()`
```php
app()->bind('example', function () {
    return new \App\Example();
});

Route::get('/', function () {
    $example = resolve('example');

    ddd($example);
});
```

**Note: Actually you don't even have to bind to `app()` to resolve later.**
**You can simply resolve, and LARAVEL will look for that and give it to you.**

## Just ask for it:
**it will simply resolve automatically**
```php
Route::get('/', function (App\Example $example) {
    ddd($example);
})
```
And that's the power of Laravel Service Contaiiner!!!

This is called:
## `Automatic Resolution`

Sometimes you will get a `BindingResolutionException`, and that's because Laravel can't bind. In this case you have to bind explicitly by the following for it to work.
`app()->bind()`
```php
app()->bind('App\Example', function () {
    $collaborator = new \App\Collaborator();

    $foo = 'foobar';

    return new \App\Example($collaborator, $foo);
});

// And now you can resolve
```

To bind services to container, you have to do it in `Provider\AppServiceProvider.php` in the register method;

```php
class AppServiceProvider extends ServiceProvider
{
    public function register()
    {
        // $this->app->bind()
        // $this->app->singleton() => to get the same instance
        // when you resolve, else you will get new Instances every
        // time you resolve

        app()->bind('App\Example', function () {
            $collaborator = new \App\Collaborator();

            $foo = 'foobar';

            return new \App\Example($collaborator, $foo);
        });

        // SINGLETON to get the same instance-----------------------------------------------------------
        app()->singleton('App\Example', function () {
            $collaborator = new \App\Collaborator();

            $foo = 'foobar';

            return new \App\Example($collaborator, $foo);
        });
    }
}

```
