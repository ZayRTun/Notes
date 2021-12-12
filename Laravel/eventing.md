**Home**
- [Home](../index.md)
---

# Eventing Pros and Cons

When a payment is processed, what is the primary or the core actions that should take place ?  
- **Core Logic** 
  - process the payment
  - unlock the purchase
- **Side Effects - Series of *Side Effects* that would often need to occur**  
  - notify the user about the payment
  - maybe award achievement (every 6 purchases you get a new badge or discount)
    - sounds like, at some point we need to trigger the logic that will inspect the user, review their purchases and determine weather or not they qualify for this new achievement batch  
  - or maybe to stay engaged with the user
    - so maybe we schedule an email two days from now and maybe that includes a sharable coupon.

**To implement the above we can:**
- we can **procedural way** all in the controller method
- create service class
- create a use case class
  - class with the name that reflects what your doing 

**Bur Laravel got Events and Listeners**  
- **Event**
  - `ProductPurchased`
- **Listeners**
  - notify the user about the payment
  - award achievements
  - send shareable coupon to user

`php artisan event:list`
- this will list all **Events** along with their respective **Listeners**

---
`php artisan make:event ProductPurchases`
- this will create an **Event Class**
  - Notice below is a striped down version
    - removed all everything except **Server side event**
```php
<?php

namespace App\Events;

use Illuminate\Foundation\Events\Dispatchable;
use Illuminate\Queue\SerializesModels;

class ProductPurchases
{
    use Dispatchable, SerializesModels;
    public $name;

    /**
     * Create a new event instance.
     *
     * @return void
     */
    public function __construct($name)
    {
        $this->name = $name;
    }
}
```
**Quick Note: All property should be public**

## Now in your `PaymentsController@store`:
```php
<?php

namespace App\Http\Controllers;

use App\Events\ProductPurchases;
use App\Notifications\PaymentReceived;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Notification;

class PaymentsController extends Controller
{
    public function create()
    {
        return view('payments.show');
    }

    public function store()
    {       
        // Events
        // handle the core logic
            // process the payment
            // unlock the purchase
            
        ProductPurchases::dispatch('toy');
        //or they are identical
        event(new ProductPurchases('toy'));
            // listeners
            // notify the user about the payment
            // award achievements
            // send shareable coupon to user 
    }
}
```
**Listener:**  `php artisan make:listener AwardAchievement`
 
To also add the listener while creating:  
`php artisan make:listener AwardAchievement -e ProductPurchases`
- this will pre load the listener with events 

```php
<?php

namespace App\Listeners;

use App\Events\ProductPurchases;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Queue\InteractsWithQueue;

class AwardAchievement
{
    /**
     * Create the event listener.
     *
     * @return void
     */
    public function __construct()
    {
        //
    }

    /**
     * Handle the event.
     *
     * @param  ProductPurchases  $event
     * @return void
     */
    public function handle(ProductPurchases $event)
    {
        var_dump('check for new achievement');
    }
}
```
**To wire the Event and the listener:**
at: `app/Providers/EventServiceProvider.php`
```php
class EventServiceProvider extends ServiceProvider
{
    /**
     * The event listener mappings for the application.
     *
     * @var array
     */
    protected $listen = [
        Registered::class => [
            SendEmailVerificationNotification::class,
        ],

        ProductPurchases::class => [
            AwardAchievement::class,
            SendShaereableCoupon::class,
        ]
    ];
}
```
**The above registering can become hectic in the long run,**  
**Laravel can auto discover automatically...**  
At the end of the `EventServiceProvider` class add the following:
```php
public function shouldDiscoverEvents()
{
    return true;
}
```
This will tell laravel to discover event and listener automatically.  
