**Home**
- [Home](../index.md)
---
# HTML Emails using Mailable Classes

Use `php artisan make:mail ContactMe` to create a new mail Class  
After running the above command there will be a new folder called `Mail` at path: `app/Mail/ContactMe.php`

Create an HTML file for Email at: `resources/views/emails/contact-me.blade.php`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>It Works Again!</h1>
    
    <p>It seems that you intereste in our latest {{ $topic }}</p>
</body>
</html>
```

After that in the `ContactController@store`:
```php
<?php

namespace App\Http\Controllers;

use App\Mail\ContactMe;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Mail;

class ContactController extends Controller
{
    public function show()
    {
        return view('contact');
    }

    public function store()
    {
        request()->validate(['email' => 'required|email']);

        Mail::to(request('email'))->send(new ContactMe("New Laravel Course"));

        return redirect('/contact')->with('message', 'Email sent!');
    }
}
``` 

## The Mailable Class `ContactMe`
```php
<?php

namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;

class ContactMe extends Mailable
{
    use Queueable, SerializesModels;

    public $topic;
    /**
     * Create a new message instance.
     *
     * @return void
     */
    public function __construct(string $topic)
    {
        $this->topic = $topic;
    }

    /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->view('emails.contact-me');
    }
    
    // to customize the subject of the email-------------------------------------
    public function build()
    {
        return $this->view('emails.contact-me')->subject('More information about ' . $this->topic);
    }
}

```
# Remember
## In `Mailable` Classes `public` properties are **Directly** available in the `view(emails.contact-me)`
---

# MarkDown View

To use a `MarkDown` view to send email:

Modify the `build()` method in the related Mailable Class as below
```php
// User markdown instead of view
public function build()
{
    return $this->markdown('emails.contact-me')->subject('More information about ' . $this->topic);
}
```

And in the View Component:  
**This component is important `@component('mail::message')`**
```html
@component('mail::message')
    # A Heading
    
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo hic magni nihil aut distinctio quae vitae repellat? Quae, iure obcaecati?
    
    - List
    - Goes
    - Here
@endcomponent
```

**And to use a call to Action in you mail, add the following: `@component('mail::button', ['url' => 'localhost:8000/contact'])`**
```html
@component('mail::message')
# A Heading

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo hic magni nihil aut distinctio quae vitae repellat? Quae, iure obcaecati?

- List
- Goes
- Here

@component('mail::button', ['url' => 'localhost:8000/contact'])
    Visit Laravel6 
@endcomponent

@endcomponent

```

**Notice: the following convention `mail::button`, `mail::message`**  
These conventions are the same with blade components loading layout views  
The only difference is that, these `mail::button` **HTML** elements are located in the vendor directory at path : `vendor/laravel/framework/src/Illuminate/Mail/resources/views/html/button.blade.php`


**You can also use `php artisan` to generate `markdown` Mailable class**
`pa make:mail Contact --markdown=emails.contact`

This command will create a Mailable class with all the necessary methods and files to create a markdown mail.
And also because we also specified the location where the `blade template` to create, it also generated a blade file markdown ready!


## Customizing Email, the layout to match your branding (colors and all) 

**In this situation we effectively want to publish the assets to our own local project, so that we can modify an tweak them on our own.**

The following command stands true to every packages:
`php artisan vendor:publish` it allows us to publish assets from vendor packages.

```bash
➜  laravel6 pa vendor:publish --tag=laravel-mail
Copied Directory [/vendor/laravel/framework/src/Illuminate/Mail/resources/views] To [/resources/views/vendor/mail]
Publishing complete.

```
It basically copies the files from the vendor directory to resources

Once it's available to you, you can modify everything as you like, there is a theme file for all the css used in the components. Better to copy it and create a new file and place it there and also must update the file at: `config/mail.php` to use the new css files.
