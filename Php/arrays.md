**Home**
- [Home](../index.md)
---

# Arrays Methods
```php
class Post
{
    public $title;
    public $published;

    public function __construct($title, $published)
    {
        $this->title = $title;
        $this->published = $published;
    }
}

$posts = [
    new Post('My First Post', true),
    new Post('My Second Post', true),
    new Post('My Third Post', true),
    new Post('My Fourth Post', false),
];
```

## `array_filter()`
-   Allows you to filter the array

```php
$unpublishedPost = array_filter($posts, function ($post) {
    return !$post->published;
});
$publishedPost = array_filter($posts, function ($post) {
    return $post->published;
});

var_dump($unpublishedPost);
var_dump($publishedPost);

// Unpublished post
// (array) [1 element]
// 3:
//     Post (object) [Object ID #5][2 properties]
//     title: (string) "My Fourth Post"
//     published: (boolean) false

// Published post
// (array) [3 elements]
// 0:
//     Post (object) [Object ID #2][2 properties]
//     title: (string) "My First Post"
//     published: (boolean) true
// 1:
//     Post (object) [Object ID #3][2 properties]
//     title: (string) "My Second Post"
//     published: (boolean) true
// 2:
//     Post (object) [Object ID #4][2 properties]
//     title: (string) "My Third Post"
//     published: (boolean) true
```

## `array_map()`
-   Allows you to transform the array in different ways.

```php
// taking only the titles
$titles = array_map(function ($post) {
   return ['title' => $post->title];
}, $posts);

// (array) [4 elements]
// 0:
//     (array) [1 element]
//     title: (string) "My First Post"
// 1:
//     (array) [1 element]
//     title: (string) "My Second Post"
// 2:
//     (array) [1 element]
//     title: (string) "My Third Post"
// 3:
//     (array) [1 element]
//     title: (string) "My Fourth Post"
```

-   Getting only the titles and returning as array

```php
$titles = array_map(fn($post) => $post->title, $posts);

// (array) [4 elements]
//     0: (string) "My First Post"
//     1: (string) "My Second Post"
//     2: (string) "My Third Post"
//     3: (string) "My Fourth Post"
```

## `array_column()`
-   Allows you to pull an item from an array
-   `array_column()` a better way to get the titles

```php
$titles = array_column($posts, 'title');
// (array) [4 elements]
//     0: (string) "My First Post"
//     1: (string) "My Second Post"
//     2: (string) "My Third Post"
//     3: (string) "My Fourth Post"
```

##   Converting to an array

```php
foreach ($posts as $key => $post) {
    $posts[$key] = (array) $post;
}

// (array) [4 elements]
// 0:
//     (array) [2 elements]
//     title: (string) "My First Post"
//     published: (boolean) true
// 1:
//     (array) [2 elements]
//     title: (string) "My Second Post"
//     published: (boolean) true
// 2:
//     (array) [2 elements]
//     title: (string) "My Third Post"
//     published: (boolean) true
// 3:
//     (array) [2 elements]
//     title: (string) "My Fourth Post"
//     published: (boolean) false
```

-   Better use array_map to achieve the above result

```php
$posts = array_map(fn($post) => (array) $post, $posts);

// (array) [4 elements]
// 0:
//     (array) [2 elements]
//     title: (string) "My First Post"
//     published: (boolean) true
// 1:
//     (array) [2 elements]
//     title: (string) "My Second Post"
//     published: (boolean) true
// 2:
//     (array) [2 elements]
//     title: (string) "My Third Post"
//     published: (boolean) true
// 3:
//     (array) [2 elements]
//     title: (string) "My Fourth Post"
//     published: (boolean) false
```