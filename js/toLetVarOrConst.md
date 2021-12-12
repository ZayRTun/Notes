**Home**
- [Home](../index.md)
---

# To Let Var or Const
**Var gets hoisted to the top unlike let which is block level - `{}`**
```js
function fire()
{
    if (bool) {
        var foo = 'bar';

        console.log(foo);   // bar
    } else {
        console.log(foo);
        // if using let we will get - Uncaught Reference: foo is not defined
        // expected - Uncaught Reference: foo is not defined
        // but getting - undefined
        // undefined - cause var foo is getting hoisted out and top if statement
    }
}

fire(false);
```

# When to use `const let and var`
-   Default to using
    -   `let name = 'Jeff'`
-   Then later if you don't want it to be re-assignable then change it to
    -   `const name = 'Jeff'`