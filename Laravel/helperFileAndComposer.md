**Home**
- [Home](../index.md)
---

# Helper File And Composer

1. Create an `Helpers.php` at `app/helpers.php`
   ```php
   <?php
    function current_user()
    {
        return auth()->user();
    }
    ```
2. Register the file in `composer.json` in `autoload`
    ```json
    "autoload": {
        "psr-4": {
            "App\\": "app/"
        },
        "classmap": [
            "database/seeds",
            "database/factories"
        ],
        "files": [ // like this here
            "app/helpers.php"
        ]
    },
    ```
3. Then run: `composer dump-autoload` to dump and reload and the `helpers.php` should be accessible all over the app.
