**Home**
- [Home](../index.md)
---

# FILE STORAGE HEADACHE

## First in `.env` set the following 
`FILESYSTEM_DRIVER=public`

## Create symlink useing `php artisan storage:link`

## Store the file using `store()`, get the path and store it in DB
```php
$path = $request('avatar')->store('avatars');

Image::create(['path' => $path]);
```

## To view the image 
```php
<img class="w-16 h-16" src="{{'storage/' . $img->path }}" alt="Avatar">
```
 
