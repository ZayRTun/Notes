**Home**
- [Home](../index.md)
---

# Data Binding

```html
<!-- Binding -->
<body>

    <div x-data="{ message: 'Hello world'}" class="container mx-auto py-2">
        <h1 x-text="message.toUpperCase()"></h1>

        <button @click="message = 'changed !'" class="border rounded bg-orange-400 p-1">
            Click me
        </button>
    </div>

</body>
```
## One way binding
**Using `x-bind:value=""` or `:value=""` is the same**  

```html
<div x-data="{ message: 'Hello world'}" class="container mx-auto p-8">
    <h1 x-text="message.toUpperCase()"></h1>

    <input x-bind:value="message" type="text" class="border rounded">
    <input :value="message" type="text" class="border rounded">
</div>
```

## Two way binding
**Uses `x-model:value`**
```html
<!-- $name is coming from laravel/blade -->
<div x-data="{ message: 'Hello {{ $name }}'}" class="container mx-auto p-8">
        <h1 x-text="message.toUpperCase()"></h1>

        <input x-model:value="message" type="text" class="border rounded">
</div>
```

## A basic calculator useing two way binding
**Notice `x-model:value.number` it's converting `string` to `integer` so that calculation can be performed**
```html
<div x-data="{ first: 0, second: 0 }" class="container mx-auto p-8">
    <input x-model:value.number="first" type="text" class="border rounded">
    <input x-model:value.number="second" type="text" class="border rounded">
    <span x-text="first + second"></span>
</div>
```
