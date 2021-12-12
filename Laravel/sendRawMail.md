**Home**
- [Home](../index.md)
---
# Send Raw Mail

To send mail use the `Mail` Facade
```php
Mail::raw('It worked', function ($message) {
    $message->to(request('email'))
        ->subject('Hello there');
});
```

**To show the user that the email was sent, we can you the flash message**  
`Flash Message` is a data that is put in the session for exactly one request.  

`return redirect('/contact')->with('message', 'Email sent!');`

```php
public function store()
{
    request()->validate(['email' => 'required|email']);

    Mail::raw('It works', function ($message) {
        $message->to(request('email'))->subject('Hello there');
    });

    return redirect('/contact')->with('message', 'Email sent!');
}
```

**To display the flash message**  
```php
@if (session('message'))
    <div>
        {{ session('message') }}  
    </div>
@endif
```
