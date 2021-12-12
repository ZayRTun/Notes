**Home**
- [Home](../index.md)
---

# Core Concepts
## Collections

**When you query using below, you are getting an instance of Article, and you can access it's value directly.**  
`App\Article::first()`  

**But below you will get a collection**  
`App\Article::all()`

**Will fetch all tags related to first article found**
`$tags = App\Article::first()->tags;`


# Collections tips and Examples:
**Once we have a collection we almost do something like a SQL query**
```php
$tags = App\Article::first()->tags;

// this is not an SQL query but 
$tags->where('name', 'laravel');

$tags->first();

$tags->first(function ($tag) {
    return strlen($tag->name) > 3;
    });

```
## To create a Collection:
Path: `vendor/laravel/framework/src/Illuminate/Support/Collection.php`

```php
collect(['one', 'two', 'three']);

$col = collect(['one', 'two', 'three'])
=> Illuminate\Support\Collection {#3095
     all: [
       "one",
       "two",
       "three",
     ],
   }
>>> $col->first()
=> "one"
>>> $col->last()
=> "three"
>>> 
```


## Create Nested array and flatten them down
```php
>>> $col = collect(['one', 'two', 'three', ['four', 'five'], 'six'])
=> Illuminate\Support\Collection {#3112
     all: [
       "one",
       "two",
       "three",
       [
         "four",
         "five",
       ],
       "six",
     ],
   }
>>> $col->flatten()
=> Illuminate\Support\Collection {#3099
     all: [
       "one",
       "two",
       "three",
       "four",
       "five",
       "six",
     ],
   }
>>> 
```

# Usefull Collection Methods
```php
>>> filter()
>>> map()
>>> flatMap()
>>> where()
>>> merge()
```
## filter()
```php
// not distructive
>>> $cols->filter(function($col) { 
        return $col >= 5; 
    });
    
=> Illuminate\Support\Collection {#3112
     all: [
       4 => 5,
       5 => 6,
       6 => 7,
       7 => 8,
       8 => 9,
       9 => 10,
     ],
   }
   
// Another Example
 
>>> $cols->filter(function($col) { 
        return $col % 2 === 0; 
    })
=> Illuminate\Support\Collection {#3019
     all: [
       1 => 2,
       3 => 4,
       5 => 6,
       7 => 8,
       9 => 10,
     ],
   }
>>>
```

**These methods they return collection, So you can chain them**

```php
>>> $items->filter(function($item) { return $item % 2 === 0; })->map(function($item) {return $item * 3;})
=> Illuminate\Support\Collection {#3116
     all: [
       1 => 6,
       3 => 12,
       5 => 18,
       7 => 24,
       9 => 30,
     ],
   }
>>> 
```

## Group query by Tags:
**Use `Eager Loading`**
```php
>>> $articles = App\Article::with('tags')->get();
=> Illuminate\Database\Eloquent\Collection {#3213
     all: [
       App\Article {#3164
         id: 6,
         user_id: 3,
         title: " Learn Laravel",
         excerpt: "Est est error velit.",
         body: "Tenetur accusantium ullam reiciendis aut iusto voluptas qui. Eum accusamus doloremque est voluptatibus exercitationem voluptatem ipsam.",
         created_at: "2020-04-04 22:00:22",
         updated_at: "2020-04-04 22:00:22",
         tags: Illuminate\Database\Eloquent\Collection {#3071
           all: [
             App\Tag {#3229
               id: 1,
               name: "laravel",
               created_at: "2020-04-05 10:06:11",
               updated_at: "2020-04-05 10:06:21",
               pivot: Illuminate\Database\Eloquent\Relations\Pivot {#3111
                 article_id: 6,
                 tag_id: 1,
                 created_at: "2020-04-05 10:09:31",
                 updated_at: "2020-04-05 10:09:33",
               },
             },
             App\Tag {#3231
               id: 2,
               name: "php",
               created_at: "2020-04-05 10:07:52",
               updated_at: "2020-04-05 10:07:56",
               pivot: Illuminate\Database\Eloquent\Relations\Pivot {#3194
                 article_id: 6,
                 tag_id: 2,
                 created_at: "2020-04-05 10:10:08",
                 updated_at: "2020-04-05 10:10:09",
               },
             },
             App\Tag {#3235
               id: 3,
               name: "education",
               created_at: "2020-04-05 10:08:07",
               updated_at: "2020-04-05 10:08:09",
               pivot: Illuminate\Database\Eloquent\Relations\Pivot {#3202
                 article_id: 6,
                 tag_id: 3,
                 created_at: "2020-04-05 10:10:19",
                 updated_at: "2020-04-05 10:10:20",
               },
             },
           ],
         },
       },
```

**Pluck the titles**
```php
>>> $articles->pluck('title')
=> Illuminate\Support\Collection {#3227
     all: [
       " Learn Laravel",
       "Accusamus in quod voluptate ut rem.",
       "Voluptates natus pariatur id.",
       "Reiciendis perferendis debitis enim facilis sed quod ab.",
       "Aut quis quisquam quidem sit reprehenderit eaque.",
       "Adipisci rerum sed voluptatem dolor.",
       "Accusantium quaerat nulla qui debitis nihil.",
       "Maiores suscipit quae vel mollitia minima.",
       "My new laravel course",
       "My personal blog",
       "Table Plus Test",
       "Table Plus Test 2",
     ],
   }
>>> 
```


**Pluck only the Tag name**  
Notice that you have to `flatten` or `collapse` then pluck the name:
```php
>>> $articles->pluck('tags')->flatten()->pluck('name')->unique()
=> Illuminate\Support\Collection {#3133
     all: [
       "laravel",
       "php",
       "education",
       "laravel",
       "php",
       "personal",
       "laravel",
       "php",
       "education",
       "php",
       "education",
       "personal",
     ],
   }
>>> 

// Get Unique:
>>> $articles->pluck('tags')->flatten()->pluck('name')->unique();
=> Illuminate\Support\Collection {#3180
     all: [
       0 => "laravel",
       1 => "php",
       2 => "education",
       5 => "personal",
     ],
   }
>>> 
```

**U can also use dot notation**
```php

>>> $articles->pluck('tags.name')
=> Illuminate\Support\Collection {#3102
     all: [
       null,
       null,
       null,
       null,
       null,
       null,
       null,
       null,
       null,
       null,
       null,
       null,
     ],
   }
// Null cause they are a collection of tags
// So we sudo Flatten it with a `*`
// Notice the empty arrays cause some articles don't have tags assiciated with them
>>> $articles->pluck('tags.*.name')
=> Illuminate\Support\Collection {#3183
     all: [
       [
         "laravel",
         "php",
         "education",
       ],
       [
         "laravel",
         "php",
         "personal",
       ],
       [],
       [],
       [],
       [],
       [],
       [],
       [
         "laravel",
         "php",
         "education",
       ],
       [
         "php",
         "education",
         "personal",
       ],
       [],
       [],
     ],
   }
>>> 

// So we flatten them down
>>> $articles->pluck('tags.*.name')->flatten()->unique();
=> Illuminate\Support\Collection {#3174
     all: [
       0 => "laravel",
       1 => "php",
       2 => "education",
       5 => "personal",
     ],
   }
>>> 

// BONUS UPPDER CASE THEM
>>> $relevantTags = $articles->pluck('tags.*.name')->flatten()->unique()->map(function ($item) { return ucwords($item);});
=> Illuminate\Support\Collection {#3160
     all: [
       0 => "Laravel",
       1 => "Php",
       2 => "Education",
       5 => "Personal",
     ],
   }
>>> 


```
