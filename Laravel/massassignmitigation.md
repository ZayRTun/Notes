**Home**
- [Home](../index.md)
---

# Mitigate Mass Assignment Vulnerabilities

## In Model add either `$fillable` or the opposite `$guarded`

**`$fillable` allows mass assignment on fields withing the array**
```php
class Post extends Model
{
    protected $fillable = ['title', 'excerpt', 'slug', 'body'];
}
```

**`$guarded` allows mass assignment on all fields except the ones withing the array**
```php
class Post extends Model
{
    protected $guarded = ['id'];
}
```

**`$guarded = []` disable mass assignment protection entirely by an empty array**
```php
class Post extends Model
{
    protected $guarded = [];
}
