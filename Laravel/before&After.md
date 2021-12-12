**Home**
- [Home](../index.md)
---

# Before & After Hook
## Used to provide global authorization to an User or Admin or SiteOwner  

Add the `before()` method:
```php
<?php

namespace App\Policies;

use App\Conversation;
use App\User;
use Illuminate\Auth\Access\HandlesAuthorization;

class ConversationPolicy
{
    use HandlesAuthorization;

    public function before(User $user)
    {
        if ($user->id === 13) {
            return true;
        }
    }
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
**Examples:**
```php
if ($user->type === 'admin')
// or 
if ($user->role === 'admin')
```

## But for a Global Authorization it's better to define in one place that will effect all Models:
**The `boot()` method in `AuthServiceProvider`**
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

        Gate::before(function (User $user) {
            if ($user->id === 13) {
                return true;
            }
        });
    }
}
```

