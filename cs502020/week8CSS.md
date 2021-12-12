**Home**
- [Home](../index.md)
---
# CSS  

**Inline CSS style**
```html
<h1 style="color: blue; text-align: center;">Hello, world!</h1>
```
<h1 style="color: blue; text-align: center;">Hello, world!</h1>

`<p style="color: blue;">This is a Blue Paragraph</p>`
<p style="color: blue;">This is a Blue Paragraph</p>

**CSS Properties**
- color: blue;
- text-align: center;
- font-size: large;
- background-color: blue;
- border: 1px solid black;
    
**Linking a stylesheet**  
`<link rel="stylesheet" href="style.css">`  
```html
<head>
    <style>
        table
        {
            border: 1px solid black;
        }
        td
        {
            border: 1px solid black;
        }
        th
        {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <h1>This is h1</h1>
</body>
```  
<head>
    <style>
        table
        {
            border: 1px solid black;
        }
        td
        {
            border: 1px solid black;
        }
        th
        {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <th>Cell 1</th>
            <th>Cell 2</th>
            <th>Cell 3</th>
        </tr>
        <tr>
            <td>Cell 4</td>
            <td>Cell 5</td>
            <td>Cell 6</td>
        </tr>
        <tr>
            <td>Cell 4</td>
            <td>Cell 5</td>
            <td>Cell 6</td>
        </tr> 
    </table>
</body>  

---