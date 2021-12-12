**Home**
- [Home](../index.md)
---

# Laravel Service Provider

Laravel framework is divided into components and each component includes a service provider.  

All Laravel component with their relative service provider can be found in the following path:  
`vendor/laravel/framework/src/Illuminate`  

**A service provider provides it's service to framework**
It may need to register `keys` in the service container or it might need to trigger some functionality after the **framework** has been booted.
___

**Any service provider can implement 2 methods:**  
- register()
  - is for registering `keys` into the service container
  - ```php
    protected function registerNativeFilesystem() 
    {
        $this->app->singleton('keyName', function () {
            return new ExampleClass;
        }); 
    }
    ```
- boot()
  - will be triggered after every single service provider in the framework has been registered. 


They are all declare in: `config/app.php`

Note: If you want to trigger some functionality after the framework has been registered, use the `boot()` method.
```php
public function boot()
{
    // this method will be called after the framework has been
    // registered
}
```
---
**If the key is `"files"`**
You can resolve it using:
`app('files')->get(public_path('index.php'));`  

## Facades are simply calling the registered `keys` under the hood, through a function called `getFacadeAccessor()`
```php
class File extends Facade
{
    protected function getFacadeAccessor()
    {
        return 'files';
    }
}
```
---

# You can create your own Facade
How to:
```php
namespace App;

class Example
{
    public function handle()
    {
        die('it works');
    }
}
```
A proxy facade for the Example class:
```php
namespace App;

use Illuminate\Support\Facades\Facade;

class ExampleFacade extends Facade
{
    protected function getFacadeAccessor()
    {
        return 'example';
    }
}
```
One more step for this to work:
- you can create you own service provider using `php artisan make:provider YourServiceProviderName`
- or you can just store it in the `app/Providers/AppServiceProvider.php` 

And therein will be the two methods from above the `register()` and the `boot()`

```php
public function register()
{
    // if you have a constructor in the `Example` class and needs to something to instantiate
    // then you have provide that explicitly below: 
    $this->app->bind(Example::class, function () {
        return new Example('someRequiredValue');
    })
    
    $this->app->bind('example', function () {
        return new Example();
    })
}

public function boot()
{

}
```
Now that we have registered the `key` into the service container, we can `resolve()`.
```php
>>> App\ExampleFacade::handle();
it works
```
