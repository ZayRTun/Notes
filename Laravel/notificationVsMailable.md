**Home**
- [Home](../index.md)
---

# Notifications Versus Mailable

There is one other way that we can notify a user and that `Notification`

To create a notification Class with pre loaded methods:
`php artisan make:notification PaymentReceived`

Now in the `PaymentsController@store` use `Notification Facade` to send off.
```php
<?php

namespace App\Http\Controllers;

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
        // this is good for a group of users
        Notification::send(request()->user(), new PaymentReceived());
    }
    
    // Or You Can use this too...
    public function store()
    {
        // this is good if for a single user
        request()->user()->notify(new PaymentReceived());

        return redirect('/payments/create');
    }
}
```

You can also format the notification mail:  
`toMail()` maps to the mail the user will received.
```php
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

```

```php
<?php

namespace App\Notifications;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Notifications\Messages\MailMessage;
use Illuminate\Notifications\Notification;

class PaymentReceived extends Notification
{
    use Queueable;

    /**
     * Create a new notification instance.
     *
     * @return void
     */
    public function __construct()
    {
        //
    }

    /**
     * Get the notification's delivery channels.
     *
     * @param  mixed  $notifiable
     * @return array
     */
    public function via($notifiable)
    {
        return ['mail'];
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
            //
        ];
    }
}


```

