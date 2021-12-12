**Home**
- [Home](../index.md)
---

# Two way data binding

## 2 approached to 2 way binding
**Using the `x-model=""` or `@input="name = $event.target.value" :value="name"`**
```html
<form action="#" x-data="{name: 'John Doe'}">
    <div class="mb-6">

        <!-- Simpler and preferred for 2 way binding -->
        <input 
            x-model="name" /
            class="border border-gray-400 p-2 w-full" 
            type="text" 
            name="name" 
            id="name" 
            required
        >
        
        <!-- This is whats happening behind the sceen -->
        <input 
            @input="name = $event.target.value" 
            :value="name" 
            class="border border-gray-400 p-2 w-full" 
            type="text" 
            name="name" 
            id="name" 
            required
        >
    </div>

    <p x-text="name"></p>
</form>
```

## Approach to `FORMs` with Alpine JS
**Note how it's submited and also using the `FORM` object to pack all form data**
**Also using the `fetch()` api**
```html
<body>
    <div class="container mx-auto px-8 flex justify-center">
        <form action="#" x-data="{
                form: {
                    name: '',
                },
                user: null,
                submit() {
                    fetch('https:/reqres.in/api/user', {
                        method: 'POST',
                        headers: {'Content-Type': 'application/json'},
                        body: JSON.stringify(this.form)
                    })
                    .then(response => response.json())
                    .then(user => this.user = user);
                }
            }" @submit.prevent="submit">

            <div class="mb-6">
                <label class="block mb-2 uppercase font-bold text-xs text-gray-700" for="name">Name</label>

                <input x-model="form.name" class="border border-gray-400 p-2 w-full" type="text" name="name" id="name" required>
            </div>

            <button class="border rounded bg-blue-400 p-1">Submit</button>

            <template x-if="user">
                <div x-text="`The user ${user.name} was create at ${user.createdAt}`"></div>
            </template>
        </form>
    </div>
</body>
```
