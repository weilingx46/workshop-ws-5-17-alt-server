# CS52 Workshop:  Building a Flask Web App

![](img/flask.png)

TODO:
Brief motivation here as well as in presentation

## Overview

We're going to build a very simple web app with Python using a micro-framework called Flask. Here's an overview of what you're going to accomplish by the end of this workshop:

TODO:

* [ ] can be checkboxes
* [ ] can be checkboxes
* [ ] can be checkboxes
* [ ] can be checkboxes

## Setup

Install Flask using the command below:

```
$ pip install Flask
```

That was easy, wasn't it? And it doesn't get much harder!

## Step by Step

### Step 1 - Hello World

Fork this repo.

Create a file called **hello.py** and copy the following code into the file:

```
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run()
```

Flask uses Python, so spacing/tabs/indents matter! Run your web app to make sure that everything's working:

```
$ python hello.py
```

Open http://localhost:5000/ in your web browser. It should look something like this:

TODO:
![hello world](url)

Congratulations, you've created a web app using Flask!

### Step 2 - Creating URL Routes

TODO:
Something about how routes are simple to set up using Flask.

We're going to be creating the following routes:

```
/hello
/members/
/members/name/
```
Create a file called **app.py** and copy the following code into the file:

```
from flask import Flask
app = Flask(__name__)

@app.route("/")
def index():
    return "Flask App!"

@app.route("/hello")
def hello():
    return "Hello World!"

@app.route("/hello/<string:name>/")
def getMember(name):
    return "Hello " + name + "!"

if __name__ == "__main__":
    app.run()
```

Restart the application by running `python app.py` on your terminal. Try out these URLS in your browser:

* http://localhost:5000/
* http://localhost:5000/hello
* http://localhost:5000/hello/Jordan

Your web browser should look something like this for the */hello/Jordan* route:

TODO:
![hello Jordan](Jordan)

### Step 3 - Styling

We're going to separate out our Flask code and HTML/CSS using templates. Make a directory called **templates**. Inside this folder, create a template called **template.html** and copy the following code into the file:

```
{% extends "layout.html" %}
{% block body %}

<div class="block1">
<h1>Hello {{name}}!</h1>
  <h2>Here is an interesting quote for you: </h2>
  <p>
"The limits of my language are the limits of my mind. All I know is what I have words for."
  </p>
<img src="http://www.naturalprogramming.com/images/smilingpython.gif">
</div>
{% endblock %}
```

Then, in the same folder, create a file called **layout.html** and copy the following code into the file:

```
<html>
<head>
    <title>Website</title>
<style>
@import url(http://fonts.googleapis.com/css?family=Amatic+SC:700);

body{
    text-align: center;    
}
h1{
    font-family: 'Amatic SC', cursive;
    font-weight: normal;
    color: #8ac640;
    font-size: 2.5em;
}

</style>

</head>
<body>
 {% block body %}{% endblock %}

</body>
</html>
```

It's technically best practice to NOT have your HTML and CSS in the same file, but we'll just keep it like this for the sake of having one less file :sunglasses:.

Finally, adjust your **app.py** file so that the code looks like this:

```
from flask import Flask, flash, redirect, render_template, request, session, abort

app = Flask(__name__)

@app.route("/")
def index():
    return "Flask App!"

@app.route("/hello")
def hello_world():
    return "Hello World!"

@app.route("/hello/<string:name>/")
def hello(name):
    return render_template(
        'template.html',name=name)

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=80)
```

Now run `python app.js` again and type in the URL http://localhost/hello/YOUR_NAME. It should look something like this:

TODO:
![hello yourname](your name)



## Summary / What you Learned

* [ ] can be checkboxes

## Resources

* cite any resources


:sunglasses: GitHub markdown files [support emoji notation](http://www.emoji-cheat-sheet.com/)

Here's a resource for [github markdown](https://guides.github.com/features/mastering-markdown/).
