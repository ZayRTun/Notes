**Home**
- [Home](../index.md)
---

# Factory

## Tinker
**using factory to seed table with fake datas**
```php
>>> factory(App\User::class)->create();
>>> factory(App\User::class, 5)->create(); // to create 5 users

>>> factory(App\Articles::class, 5)->create(['title' => 'Override the title']); // overriding the title
>>> factory(App\Articles::class, 5)->create(['user_id' => 1]); // overriding the title
```
**Create a factory**
```bash
php artisan make:factory ArticleFactory -m "App\Article"
```
**Defining a factory**
```php
$factory->define(Article::class, function (Faker $faker) {
    return [
        'user_id' => factory(\App\User::class), // this will create a user get the id
        'title' => $faker->sentence,
        'excerpt' => $faker->sentence,
        'body' => $faker->paragraph,
    ]
});


// Foreign key constraints for not leaving any orphaned data when the user is deleted

public function up()
{
    Schema::create('articles', function(Blueprint $table) {
        $table->bigIncrements('id');
        $table->unsignedBigInteger('user_id');
        $table->string('title');
        $table->text('excerpt');
        $table->text('body');

        // When a user is deleted the associated articles will also be deleted
        $table->foreign('user_id)
            ->references('id)
            ->on('users)
            ->onDelete('cascade);

    })
}
// to make an eloquent query you call the method as a property

$user = new App\User::find(1);
$user->articles;
```
