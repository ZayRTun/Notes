**Home**
- [Home](../index.md)
---

# Toggle Visibility Using State

**Notice using `x-on:click=""` and `@click=""`**
```html
<div x-data="{ show: false }">
        <h1 x-show="show">Hello World</h1>

        <button x-on:click="show = ! show">Toggle</button>
        <button @click="show = ! show" x-text="show ? 'Hide' : 'Show'"></button>
    </div>
```

## Creating Tabs in 5 mins
```html
<body>
    <div x-data="{ currentTab: 'first' }">
        <div class="mt-4 pl-2">
            <div @click="currentTab = 'first'" :class="{'bg-gray-300 outline-none' : currentTab === 'first'}" class="px-2 outline-none inline-block rounded-t cursor-pointer">First</div>
            <div @click="currentTab = 'second'" :class="{'bg-gray-300 outline-none' : currentTab === 'second'}" class="px-2 outline-none inline-block rounded-t cursor-pointer">Second</div>
            <div @click="currentTab = 'third'" :class="{'bg-gray-300 outline-none' : currentTab === 'third'}" class="px-2 outline-none inline-block rounded-t cursor-pointer">Third</div>
        </div>
        <div class="w-full rounded bg-gray-300 py-16 px-4">
            <div x-show="currentTab === 'first'">First Tab</div>
            <div x-show="currentTab === 'second'">Second</div>
            <div x-show="currentTab === 'third'">Third</div>
        </div>
    </div>
</body>

```
