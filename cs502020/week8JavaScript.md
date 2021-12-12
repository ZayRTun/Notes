**Home**
- [Home](../index.md)
---

# JavaScript  
JavaScript, a language that browsers can interpret and run, with syntax similar to that of C.

A variable in C
```C
int i = 0;
```  
A variable in JavaScript
```javascript
let i = 0;
```

A for loop in C
```c
for (int i = 0; i < 50; i++)
{

}
```

A for loop in JavaScript
```javascript
for (let i = 0; i < 50; i++)
{

}
```


A function in C
```c
void cough(int n)
{
    
}
```

A function in JavaScript
```javascript
function cough(n)
{
    
}
```

## Why JavaScript ?  
**DOM** Document Object Model  

JavaScript, when run inside a browser has the ability to manupilate the DOM. Ability to look at the DOM, the structure of the Webpage, **extract parts of it, replase parts of it and update parts of it**.

**Getting** the value from an HTML element with the ID of **name**
`let name = document.querySelector('#name').value;`  

**Setting** the value of an HTML element with the ID of **return**
`document.querySelector('#result').innerHTML = name;`


**Selectable options**
```html
<body>
    <p id="para">This is some text.</p>
    <select>
        <option value="large">Large Test</option>
        <option value="initial" selected>Medium Test</option>
        <option value="small">Small Test</option>
    </select>
</body>
```
JS Script
```javascript
document.querySelector('select').onchange = function() {
    document.querySelector('p').style.fontSize = this.value;
}
```

**JS Interval**
Blinking an html element like a **\<body>**  
```javascript
function blink()
{
    let body = document.querySelector('body');

    if (body.style.visibility == 'hidden') 
    {
        body.style.visibility = 'visible';
    }
    else
    {
        body.style.visibility = 'hidden';
    }
}
// blink every 500ms
window.setInterval(blink, 500);
```

**Getting Geolocation**
```javascript
navigator.geolocation.getCurrentPosition(position => {
    let lat = position.coords.latitude;
    let lon = position.coords.longitude;
    document.write(lat + '-' + lon);
});
```





