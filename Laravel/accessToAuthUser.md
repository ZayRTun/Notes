**Home**
- [Home](../index.md)
---

# Limit Access to Auth User

**To limit access to functionalities in `Blade` we can use `@can()`**

```php
@can('update-conversation', $conversation)
    <form action="" method="post">
        <button type="submit" class="btn p-0 text-muted">Best Reply?</button>
    </form>
@endcan
```
Now at: `app/Providers/AuthServiceProvider.php` we specify a `Gate` **facade**  in the `boot()` method
```php
<?php

namespace App\Providers;

use App\Conversation;
use App\User;
use Illuminate\Foundation\Support\Providers\AuthServiceProvider as ServiceProvider;
use Illuminate\Support\Facades\Gate;

class AuthServiceProvider extends ServiceProvider
{
    /**
     * The policy mappings for the application.
     *
     * @var array
     */
    protected $policies = [
        // 'App\Model' => 'App\Policies\ModelPolicy',
    ];

    /**
     * Register any authentication / authorization services.
     *
     * @return void
     */
    public function boot()
    {
        $this->registerPolicies();

        Gate::define('update-conversation', function (User $user, Conversation $conversation) {
            return $conversation->user->is($user);
        });
    }
}
```

**Notice!!**   
```php
Gate::define('update-conversation', function (User $user, Conversation $conversation) {
    return $conversation->user->is($user);
});`
```
it's checking if the `conversation user(creator) is the current logged in user`>> if true >> logged in user will have access to functionalities.  

You define a key `update-conversation` the you can reference this key in your `views`. 

## Authorization in the Controller
```php
<?php

namespace App\Http\Controllers;

use App\Reply;
use Illuminate\Http\Request;

class ConversationBestReplyController extends Controller
{
    public function store(Reply $reply)
    {
        $this->authorize('update-conversation', $reply->conversation);

        $reply->conversation->best_reply_id = $reply->id;

        $reply->conversation->save();

        return back();
    }
}
```

**There are other ways to handle Authorizations in Laravel**  
The above can also be done as follows:  
```php
class ConversationBestReplyController extends Controller
{
    public function store(Reply $reply)
    {
        
        if (Gate::denies('update-conversation', $reply->conversation)) {
            die('We can handle it this way');
        }

        $reply->conversation->best_reply_id = $reply->id;

        $reply->conversation->save();

        return back();
    }
}
```
### Often you'll reach for this if you need specialize how you respond, weather it's a custom redirect or response  

Note:: using `$this->authorize()` is not unique, it's still delegating to that same `Gate` facade.  

___

# Policies

Storing all of your authorization logic in the `AuthServiceProvider` boot() method can get over whelming to manage cause it can get really long.

## Policy is a class that encapsulates an `Authorization` policy for a Model

**To create a Policy class**
`php artisan make:policy ConversationPolicy --model=Conversation`

```php
<?php

namespace App\Policies;

use App\Conversation;
use App\User;
use Illuminate\Auth\Access\HandlesAuthorization;

class ConversationPolicy
{
    use HandlesAuthorization;

    /**
     * Determine whether the user can update the model.
     *
     * @param  \App\User  $user
     * @param  \App\Conversation  $conversation
     * @return mixed
     */
    public function update(User $user, Conversation $conversation)
    {
        return $conversation->user->is($user);
    }
}
```
## Now the `update()` will be called from the `store()` method in the `ConversationBestReplyController` controller.
```php
class ConversationBestReplyController extends Controller
{
    public function store(Reply $reply)
    {
        $this->authorize('update', $reply->conversation);

        $reply->conversation->best_reply_id = $reply->id;

        $reply->conversation->save();

        return back();
    }
}
```
### Also in our view, no longer use `update-conversation`, we use `update`:
```php
@can('update', $conversation)
    <form action="/best-replies/{{ $reply->id }}" method="post">
        @csrf
        
        <button type="submit" class="btn p-0 text-muted">Best Reply?</button>
    </form>
@endcan
```
