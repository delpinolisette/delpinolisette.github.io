---
layout: default
title: Python and Flash Quick Start
---
### Getting a Python Web Application up and Runing with Flask

These are instructions for getting a Python web app up and running quickly with Flask. **On Windows!!** On MacOS/ Linux, commands differ slightly but can be easily found online. 

Why Flask? A micro web framework written in Python. It's doesn't have a databse abstraction layer or form validation, but it is quick and easy!
Also it was writtein in 2010 by Armin Ronacher (at a very young age!).

Steps: as of 2020-07-08 16:13:

#### **Step 1: Setting Up Virtualenv and Installing Packages:**
1. make sure Python 3+ installed with ``python -V`` 
2. install pip. with pip, ``pip3 install virtualenv``, so that your packages are installed locally rather than globally. This is better for portability and collaboration.
3. make and environment with ``virtualenv env`` but name the env whatever you want.
4. select source with ``env\Scripts\activate``, make sure you are running Powershell with admin priviliges! You should be inside ``env`` now. 
5. ``pip3 install flask flask-sqlalchemy``

#### **Step 2: Writing Your Application :** 
1. Make a .py file, ``MyApp.py``
2. Inside ``MyApp.py``: 
3. Import Flask
4. refer to the app. with ``MyApp = Flask(__name__)``
5. Set up routes, first, the index. 
6. Define the function for route. (Right now it's just "Hello World")
7. In development, set debug = true. This will show any errors. 
8. Steps 2-7 are summarized here:

``` python
from flask import Flask

MyApp = Flask(__name__)

@MyApp.route('/')

def index():
  return "Hello World" 
  # remember to be consistent with your spacing. 
  # I chose 2 spaces. 

if __name__== "__main__":
  MyApp.run(debug = True)

```

9. make sure you're still in ``(env)`` and run your code with ``py MyApp.py``. 
10. Navigate to ``localhost:5000`` to see your app. 
11. Congratulations! You're up and running !

### **Step 3: Customizing your app:**

1. It's a good idea to use templates and html inheritance - Don't Repeat Yourself. Make a ``templates`` folder, and a ``static`` folder. 
    * Template will live in the former and css/static content will live in the latter. 
2. import ``render_template`` in ``MyApp.py``
3. Once imported, you can go into the ``index()`` function and call ``render_template('index.html')`` from your templates folder. After running your app, the homepage shold be updated. Now you know how to inject a template!

### **Step 3b: HTML Inheritance :**
1. Let's make a template that is inherited by any other pages in the site we wish:
    * Go to ``templates`` folder and make a ``base.html`` file. 
    * Write boilerplate html into your ``base.html``. Good source for this is: [html shell](http://htmlshell.com/)
    * Now let's use Jinja2 syntax, full documentation [here](https://jinja.palletsprojects.com/en/2.11.x/), since it's based off Django templating. (Also, it's the template engine for Flask!)
    * insert ``{% block head %}{% endblock %}`` before end of head tag.
    * insert ``{% block body %}{% endblock %}`` before end of body tag.
    * Between these, this will be where content is inserted. 
2. Your ``base.html`` should now resemble this:

``` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    {% block head %}{% endblock %}
  </head>
  <body>
    {% block bpdy %}{% endblock %}
  </body>
</html>
```

3. Now navigate back to ``index.html`` and clear it so that you can inherit from ``base.html``. 
4.  Extend base by writing ``{% extends `base.html` %}`` (Don't forget single quotes.)
5.  Next, inject your styling into base by writing ``{% block head %} <p> your content here</p> {% endblock %}`` and similarly, ``{% block body %} <p> your content here</p> {% endblock %}``
6.  Now your ``index.html`` template should be: 

``` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    {% block head %}{% endblock %}
  </head>
  <body>
    {% block bpdy %}{% endblock %}
  </body>
</html>
```

### **Step ??: HTTP Requests** (TODO)
1. to use HTTP requests, first learn the general structure of one....TBC

### **Step ??: Forms (TODO)**
1. To have forms on your web app, install Flask-WTF for forms. 
2. in your ``env``, install by ``pip install flask-wtf``
3. Now you need to store a `SECRET KEY`. :
    * It's good practice to have a separate configuration page for all your variabled, but since this is presumably your first Flask app, go ahead and write it in ``MyApp.py`` for simplicity. 
    * Under ``MyApp = Flask(__name__)``, write ````




### Sources : 
1. [Forms](https://www.youtube.com/watch?v=-O9NMdvWmE8)
2. [In-depth Forms](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iii-web-forms)
2. [Flask](https://www.youtube.com/watch?v=Z1RJmh_OqeA)
3. My brain
