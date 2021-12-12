**Home**
- [Home](../index.md)
---

# Laravel Route
**Laravel Ide Helper Gist:**

Wget the link below:
(https://gist.githubusercontent.com/barryvdh/5227822/raw/4be028a27c4ec782965bb8f2fdcb4c08c71a441d/_ide_helper.php)


## Update highlight nav links
Request::path() === '/' ? 'current_page_item' : ''
// or you can also do
Request::is('about') ? 'current_page_item' : ''

```php
<li class="{{ Request::path() === '/' ? 'current_page_item' : '' }}">
    <a href="/" accesskey="1" title="">Homepage</a>
</li>
```

**querying in the closure in web.php**
```php
Route::get('/about', function() {
    //Examples
    return  $articles = Article::paginate(3);
    return  $Article::latest()->paginate(3);
    return  $articles = Article::take(2)->get();
    return  $articles = Article::all(3);
    return  $articles = Article::first(3);
    return view('about', compact('articles'));
});
```

## Restful routing
**GET, POST, PUT, PATCH, DELETE**

// GET /articles
// GET /articles/{id}
// POST /articles
// PUT /artilces/{id}
// DELETE /articles/{id}

// GET /videos
// GET /videos/create
// POST /videos
// GET /videos/2
// GET /artilces/2/edit
// PUT /artilces/2
// DELETE /videos/2

```php
Route::get('/articles', 'ArticleController@index');
Route::post('/articles', 'ArticleController@store');
Route::get('/articles/create', 'ArticleController@create');
Route::get('/articles/{article}', 'ArticleController@show');
Route::get('/articles/{article}/edit', 'ArticleController@edit');
Route::put('/articles/{article}', 'ArticleController@update')
```

## Named Routes
```php
Route::get('article/{article}', 'ArticleController@show')->name('articles.show');

<a href="{{ route('articles.show', $article->id) }}">Articles</a>
// or pass the article it self
<a href="{{ route('articles.show', $article) }}">Articles</a>

// or define a path() method in the Model class
public function path()
{
    return route('articles.show', $this);
}
// then in controller, redirect using this method
return redirect($article->path());

// also
<a href="{{ $article->path() }}">Articles</a>
```
---

# Validate Create & Update
**Validation**
```php
request()->validate([
    'title' => 'required'|min:3,
    'excerpt' => 'required',
    'body' => 'required'
]);

Article::create(request()->validate([
    'title' => 'required',
    'excerpt' => 'required',
    'body' => 'required'
]));

$article->update(request()->validate([
    'title' => 'required',
    'excerpt' => 'required',
    'body' => 'required'
]));
```

## Display Validation Error message
```php
// $errors->first('title')

<div class="form-group">
    <label for="title">Title</label>
    <input class="@error('title') is-invalid @enderror form-control" type="text" id="title" name="title">
    <p class="is-invalid text-danger">{{ $errors->first('title') }}</p>
</div>

// options

<div class="form-group">
    <label for="title">Title</label>
    <input class="@error('title') is-invalid @enderror form-control" type="text" id="title" name="title">

    @if ($errors->has('title'))
        <p class="is-invalid text-danger">{{ $errors->first('title') }}</p>
    @endif

    @error('title')
        <p class="is-invalid text-danger">{{ $errors->first('title') }}</p>
    @enderror

    // getting the original value
    <input class="@error('title') is-invalid @enderror form-control" type="text" id="title" name="title"
                    value="{{ old('title') }}">
</div>
```

**Mass assignment setting in Class**
```php
protected $fillable = ['title', 'excerpt', 'body'];
// change to
protected $guarded = [];
```


