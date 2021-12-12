**Home**
- [Home](../index.md)
---
# Eloquent

## Eloquent Relationships
```php
class User {

    public function articles()
    {
        return $this->hasMany(Articles::class); // select * from articles where user_id =
    }

    public function projects()
    {
        return $this->hasMany(Projects::class);
    }
    // you need to have a user_id column in projects database so as in Articles database for this to work
}

class Projects {

    public function user()
    {
        return $this->belongsTo(User::class);
    }
}

// hasOne
// hasMany
// belongsTo
// belongsToMany
// there are many more but above 4 is good enough for many cases
```  
