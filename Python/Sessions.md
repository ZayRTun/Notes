**Home**
- [Home](../index.md)
---  
# Sessions
Recall that cookies are small files that websites ask our browser to store on our computer, with some kind of identifier that our browser shows the website the next time we go there, so the website knows who we are. This allows our server to have **sessions**, or data for users’ interactions with a website, specific to each of them.  

To solve this, we can use sessions from Flask, by importing and initializing their implementation
**To configure a Session**
```python
from flask import Flask, render_template, session
from flask_session import Session

app = Flask(__name__)
app.config['SESSION_PERMANENT] = False
app.config['SESSION_TYPE] = 'filesystem'
Session(app)

@app.route('/')
def tasks():
    return render_template('tasks.html')

```
