**Home**
- [Home](../index.md)
---

# The new Arrow Syntax
```js
class TaskCollection {
    constructor(tasks = [])
    {
        this.tasks = tasks;
    }

    log()
    {
        // Arrow syntax make inline functions shorter
        this.tasks.forEach(task => console.log(task));

    }
}

class Task {}


new TaskCollection([
    new Task,
    new Task,
    new Task
]).log();
```