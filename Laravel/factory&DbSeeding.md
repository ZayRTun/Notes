**Home**
- [Home](../index.md)
---
# Factory & DB Seeding

Link to `$faker`: (https://github.com/fzaninotto/Faker)  

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
```
## Using Seed Classes
**To Create a Seeder Class**  
- `php artisan make:seeder ConversationSeeder`  

```php
<?php

use Illuminate\Database\Seeder;

class ConversationSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        factory(App\Conversation::class, 3)
            ->create()
            ->each(function ($conversation) {
                $conversation->replies()->createMany(
                    factory(App\Reply::class, 3)->make()->toArray()
                );
            });
    }
}
```
**Notice!!!**  
The above factory is using `RelationShip` to create 3 **Reply** on **each** **Conversation**

