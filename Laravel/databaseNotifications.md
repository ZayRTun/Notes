**Home**
- [Home](../index.md)
---

# Database Notifications

**First we tried the `Mail` channel for notifications. Sending only mails to notify User**  
**Here we will try `Database Notification` for storing and notifying the user**

Create a `Notification Table` for storing the *read state* and *data*:
## `php artisan notifications:table`  
## `php artisan migrate`  
- These will create a Notification table and migrate

---


## Next we update the `PaymentReceived extends Notification` class's `via()` method:
- **Notice:** added a `database` channel in the `via()` method.
- **Notice:** accepting an `$amount` in the constructor for storing in `Notifications Table`.
- **Notice:** `toMail()` and `toArray()`.
  - `toMail()` data goes to mail
  - `toArray()` data goes to database 

```php
class PaymentReceived extends Notification
{
    use Queueable;

    protected $amount;
    /**
     * Create a new notification instance.
     *
     * @return void
     */
    public function __construct($amount)
    {
        $this->amount = $amount;
    }

    /**
     * Get the notification's delivery channels.
     *
     * @param  mixed  $notifiable
     * @return array
     */
    public function via($notifiable)
    {
        return ['mail', 'database'];
    }

    /**
     * Get the mail representation of the notification.
     *
     * @param  mixed  $notifiable
     * @return \Illuminate\Notifications\Messages\MailMessage
     */
    public function toMail($notifiable)
    {
        return (new MailMessage)
            ->subject('Your Laravel payment was received.')
            ->greeting("What's up?")
            ->line('The introduction to the notification.')
            ->line('Lorem The introduction to the notification. Lorem The introduction to the notification.')
            ->action('Sign Up', url('/'))
            ->line('Thank you!');
    }

    /**
     * Get the array representation of the notification.
     *
     * @param  mixed  $notifiable
     * @return array
     */
    public function toArray($notifiable)
    {
        return [
            'amount' => $this->amount,
        ];
    }
}
```
---
# User view Notification
**Route**
`Route::get('/notification', 'UserNotificationsController@show')->middleware('auth');`  

**`UserNotificationsController@show`**  
- **Notice:** getting only `unreadNotifications`  
- **Notice:** after getting `markAsRead()` cause the user will be viewing
- You can get all **notifications** by simply `auth()->user()->notifications` 


```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class UserNotificationsController extends Controller
{
    public function show()
    {
        $notifications = auth()->user()->unreadNotifications;

        $notifications->markAsRead();

        return view('notifications.show', [
            'notifications' => $notifications
        ]);
    }
}
```
**using `tap()` for above `show()` method** *which makes the code much cleaner*
```php
public function show()
{
    return view('notifications.show', [
        'notifications' => tap(auth()->user()->unreadNotifications)->markAsRead();
    ]);
}
```

## Front-End for notifications

```php
@extends('layouts.app')


@section('content')
    <div class="container">
        <ul>
            @forelse ($notifications as $notification)
                <li>
                    @if ($notification->type === "App\Notifications\PaymentReceived")
                        We have received ${{ $notification->data['amount'] / 100 }} from you.</br>
                    @endif
                </li>
            @empty
                <li>You have no unread notifications at this time.</li>
            @endforelse
        </ul>
    </div>
@endsection
```
