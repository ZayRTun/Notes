**Home**
- [Home](../index.md)
---

# Hello World

Basic setup with CDN
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        {{ greeting }}
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

    <script>
        new Vue({
            el: '#app',
            data: {
                greeting: 'Hello from vue'
            }
        });
    </script>
</body>

</html>
```

# Data Binding
## One way
**To Bind data use `v-bind:value="email"`**  
Short form  
## `v-bind` === `:` === `:value="value"`

## Two way
`v-model:value="email"`

# Methods
```html
<button type="submit" v-on:click="process" class="btn btn-primary">Submit</button>

<script>
var vm = new Vue({
    el: '#app',
    data: {
        email: "john@exm.com"
    },
    // Using methods here
    methods: {
        process: function (event) {
            event.preventDefault();
            alert('Submitted ' + this.email);
        }
    }
</script>
});
```

**Prevent browser from loading:**
## `.prevent`
## `v-on:click.prevent="process"`
**Short form**
## `v-on:click="process"` === `@click="process"`


## To hide or show an html element we can use:
```html
<form v-if="! submitted" class="mt-5">
// and
<div v-if="submitted" class="mt-5">
// or
<form v-if="! submitted" class="mt-5">
// and, notice this v-else
<div v-else class="mt-5">
// or r-show
<form v-show="! submitted" class="mt-5">
// and
<div v-show="submitted" class="mt-5">
```

## To hide **Flickering**
## `v-cloak`

```html
<style>
    [v-cloak] {
        display: none;
    }
</style>

<div v-else class="mt-5" v-cloak>
    Thanks for submitting!
</div>
```

# Hooks - Vue Instance Lifecycle
- **new Vue()**  
- beforeCreate  
- created
- *before and after reactive properties and methods are set up*
- ---
- beforeMount
- mounted
- *before and after the root DOM element is replaced with Vue's version*
- ---
- beforeUpdate
- updated
- *beforeUpdate and updated usually ovvur multiple times (whenever data properties change)*
- ---
- beforeDestroy
- destroyed  
- *before and after `vm.$destroy()` is called*

