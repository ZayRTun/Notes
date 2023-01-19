- [Home](../index.md)
---
# Python Flask

**Flask** framework in Python, which allows us to write a web server with many features. 

## Installation  
**Virtual environments**
Use a virtual environment to manage the dependencies for your project, both in development and in production.

**Create an environment**  
Create a project folder and a venv folder within:
```bash
$ mkdir myproject
$ cd myproject
$ python3 -m venv venv
```  
**Activate the environment**  
Before you work on your project, activate the corresponding environment:  
```bash
$ . venv/bin/activate
```  
**Install Flask**  
Within the activated environment, use the following command to install Flask:
```bash
$ pip install Flask
```  
---
## Quickstart  

A Minimal Application

A minimal Flask application looks something like this:
```python
from flask import Flask, render_template
app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

# to run the application in debug mode so that 
# the server restarts as code changes 
if __name__ == "__main__":
    app.run(debug=True)
```  

**Multiple post methods on single route**  

*GET & POST*  
```python
todos = [] 

@app.route('/add', methods=['GET', 'POST'])
def add():
    if request.method == 'GET':
        return render_template('add.html')
    else:
        todo = request.form.get('task')
        if not todo:
            return redirect('/failure')
        todos.append(todo)
        return redirect('/')
```  


---

## Template Rendering  

`flask.render_template(template_name_or_list, **context)  `  
*  Renders a template from the template folder with the given context.*


Parameters:  
```
template_name_or_list    –      the name of the template to be rendered, or an iterable with 
                                template names the first one existing will be rendered.
context                  –      the variables that should be available in the context of the template.
```

`flask.render_template_string(source, **context)`    
*  Renders a template from the given template source string with the given context. Template variables will be autoescaped.*

Parameters:  
```
source                   –      the source code of the template to be rendered
context                  –      the variables that should be available in the context of the template.
```

**Getting user input to a form**
```python
from flask import Flask, render_template, request

@app.route('/hello')
def hello():
    name = request.args.get('name')
    if not name:
        reutrn render_template('failuar.html')

    return render_template("hello.html", name=name)
```  

**Creating a layout file to share across html pages**  
Code: layout
```html
<style>
    {% block style %}
    {% endblock %}
</style>
<body>
    {% block body%}
    {% endblock %}
</body>
```
Layout: usage
```html
{% extends 'layout.html' %}

{% block style %}
    <!-- CSS STYLE HERE -->
{% endblock %}

{% block body %}
    <!-- HTML HERE -->
{% endblock %}
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello</title>
    <style>
        {% block style %}
        {% endblock %}
    </style>
</head>
<body>
    {% block body%}
    {% endblock %}
</body>
</html>
```  

**Using the layout file in other pages**
```html
{% extends 'layout.html' %}

{% block body %}
    <form action="/hello">
        <input name="name" type="text" placeholder="Name">
        <input type="submit">
    </form>
{% endblock %}
```  