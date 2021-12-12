**Home**
- [Home](../index.md)
---

# Tailwind LaravelMix Installation

1. Install Tailwind via npm
    For most projects (and to take advantage of Tailwind's customization features), you'll want to install Tailwind via npm.
    ```
    # Using npm
    npm install tailwindcss
    ```
    In `webpack.mix.js` add the following:
    ```js
    mix.js('resources/js/app.js', 'public/js');

    mix.postCss('resources/css/main.css', 'public/css', [
        require('tailwindcss'),
    ]);
    ```
    
2. Add Tailwind to your CSS
   In the `public` folder in Laravel create `resources/css/main.css` and add the below @tailwind directives.   
   Use the @tailwind directive to inject Tailwind's base, components, and utilities styles into your CSS:
   
    ```css
    @tailwind base;

    @tailwind components;

    @tailwind utilities;
    ```

