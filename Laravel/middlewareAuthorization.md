**Home**
- [Home](../index.md)
---

# Middleware Authorization

Authorize that you view it:
```php
class ConversationPolicy
{
    use HandlesAuthorization;

    public function view(User $user, Conversation $conversation)
    {
        return $conversation->user->is($user);
    }
    
    public function edit(User $currentUser, User $user)
    {
        return $currentUser->is($user);
    }
}

// Now in your route, reference the view() method
Route::get('/conversations/{conversation}', 'ConversationController@show')->middleware('can:view,conversation');
```
## Notice: 
### `middleware('can:view,conversation')`
**You can also do**  
### `middleware('can:edit,user')`
