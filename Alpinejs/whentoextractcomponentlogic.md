**Home**
- [Home](../index.md)
---

# How and When to Extract Component Logic

## It's recommended to inline the logic
**But to extract it to a separate file cause it's too messy**
**Must assign to `window.`**
```html
<body>
    <div class="container mx-auto px-8 flex justify-center mt-2">
        <div x-data="taskApp()">
            <form @submit.prevent="submit()">
                <input
                    x-model="newtask"
                    class="border rounded p-1"
                    type="text"
                    placeholder="What to do next !"
                >
            </form>

            <ul class="list-disc mt-3">
                <template
                    x-for="(task, index) in tasks"
                    :key="index"
                >
                    <li class="flex items-center space-x-2">
                        <input
                            type="checkbox"
                            x-model:value="task.completed"
                        >
                        <span
                            x-text="task.body"
                            :class="{'line-through' : task.completed}"
                        ></span>
                    </li>
                </template>
            </ul>
        </div>
    </div>
</body>
```
## Alpine in seperate file if your working with `bundelers like laravelMix` declared in `window`
```js
window.taskApp = () => {
    return {
        tasks: [],
        newtask: '',

        submit() {
            this.tasks.push({ body: this.newtask, completed: false });
            this.newtask = '';
        }
    };
}
```
## If you have a directory `COMPONENT` like VUE
`/js/components/TaskApp.js`
```js
window.taskApp = () => {
    return {
        tasks: [],
        newtask: '',

        submit() {
            this.tasks.push({ body: this.newtask, completed: false });
            this.newtask = '';
        }
    };
}
```
**This how to import it in the entry file `app.js`**
```js
import './components/TaskApp';
```

### If returning a module like VUE does:
```js
export default () => {
    return {
        tasks: [],
        newtask: '',

        submit() {
            this.tasks.push({ body: this.newtask, completed: false });
            this.newtask = '';
        }
    };
}
```
### Then in entry file `app.js` import it as follows:
```js
import taskApp from './components/TaskApp'

window.taskApp = taskApp;
// but then again you must declare it on window
```

