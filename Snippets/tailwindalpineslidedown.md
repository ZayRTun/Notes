**Home**
- [Home](../index.md)
---

# Tailwind Alpine slide down
```html
<div x-show="show"
             x-cloak
             x-transition:enter="transition transform ease-out duration-300"
             x-transition:enter-start="scale-y-0 origin-top overflow-y-hidden"
             x-transition:enter-end="scale-y-100 origin-top"
             x-transition:leave="transition transform ease-out duration-200"
             x-transition:leave-start="scale-y-100 origin-top overflow-y-hidden"
             x-transition:leave-end="scale-y-0 origin-top"
             class="py-3 bg-gray-900 space-y-3">
            <a class="block hover:bg-gray-700 px-3" href="#">Links 1</a>
            <a class="block hover:bg-gray-700 px-3" href="#">Links 2</a>
            <a class="block hover:bg-gray-700 px-3" href="#">Links 3</a>
            <a class="block hover:bg-gray-700 px-3" href="#">Links 4</a>
        </div>
```