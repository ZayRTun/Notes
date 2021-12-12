**Home**
- [Home](../index.md)
---

# Data Tables

## Creating a macro
**For building query macro**
- `Properties:search('title', '$this->search)->paginate(10);`

### In `AppServiceProvider.php` boot add method below:
```php
Builder::macro('search', function ($field, $string) {
    return $string ? $this->where('$field', 'like', '%'.$string.'%') : $this;
});
```

# Note:
- You can sleep/stop a method flow using
- `sleep(1)`