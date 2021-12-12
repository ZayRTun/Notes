**Home**
- [Home](../index.md)
---

# Transitions 101

## Out of the box transition, duration & scale
```html
<div
    x-show.transition="show"
    class="bg-green-400 w-full h-full"
></div>

<!-- duration 5 seconds-->
<div
    x-show.transition.duration.5000ms="show"
    class="bg-green-400 w-full h-full"
></div>

<!-- scale to & from 0 -->
<div
    x-show.transition.duration.5000ms.scale.0="show"
    class="bg-green-400 w-full h-full"
></div>
```

## To have full control over the transition:
**though a bit of duplication but still works**
```html
<div
    class="bg-green-400 w-full h-full"
    x-show="show"
    x-transition:enter-start="transition duration-1000 opacity-0"
    x-transition:enter-end="transition duration-1000 opacity-100"
></div>
```

### Reduce duplication by
```html
<div
    class="bg-green-400 w-full h-full"
    x-show="show"
    x-transition:enter="transition duration-75"
    x-transition:enter-start="opacity-0"
    x-transition:enter-end="opacity-100"
></div>
```

### All the transition controls
```html
<div
    class="bg-green-400 w-full h-full"
    x-show="show"
    x-transition:enter="transition transform duration-1000 ease-in"
    x-transition:enter-start="opacity-0 scale-110"
    x-transition:enter-end="opacity-100 scale-100"
    x-transition:leave="transition transform duration-200"
    x-transition:leave-start="opacity-100 scale-150"
    x-transition:leave-end="opacity-0 scale-0"
></div>
```

## Real world Transitioning Example
```html
<body>
    <div class="grid items-center justify-center h-screen">

        <div
            x-data="{show: false}"
            @click.away="show = false"
        >
            <button
                class="focus:outline-none"
                @click="show = !show"
            >Links</button>

            <div
                class="absolute bg-black text-white rounded py-2 mt-1"
                x-show="show"
                x-transition:enter="transition transform duration-150 ease-out"
                x-transition:enter-start="opacity-0 scale-75"
                x-transition:leave="transition transform duration-100 ease-in"
                x-transition:leave-end="opacity-0 scale-75"
            >
                <a
                    class="block hover:bg-gray-800 text-sm px-2"
                    href="#"
                >Edit</a>
                <a
                    class="block hover:bg-gray-800 text-sm px-2"
                    href="#"
                >Delete</a>
                <a
                    class="block hover:bg-gray-800 text-sm px-2"
                    href="#"
                >Report Spam</a>
            </div>

        </div>

    </div>
</body>

```
