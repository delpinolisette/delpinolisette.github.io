---
layout: default
title: Python and Flash Quick Start
---
### Getting a Python Web Application up and Runing with Flask

These are instructions for getting a Python web app up and running quickly with Flask. **On Windows!!** On MacOS/ Linux, commands differ slightly but can be easily found online. 

Why Flask? A micro web framework written in Python. It's doesn't have a databse abstraction layer or form validation, but it is quick and easy!
Also it was writtein in 2010 by Armin Ronacher (at a very young age!).

Steps: as of 2020-07-08 16:13:

#### Setting Up Virtualenv and Installing Packages: 
1. make sure Python 3+ installed with ``python -V`` 
2. install pip. with pip, ``pip3 install virtualenv``, so that your packages are installed locally rather than globally. This is better for portability and collaboration.
3. make and environment with ``virtualenv env`` but name the env whatever you want.
4. select source with ``env\Scripts\activate``, make sure you are running Powershell with admin priviliges! You should be inside ``env`` now. 
5. ``pip3 install flask flask-sqlalchemy``

#### Writing Your Application : 
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

### Customizing your app: 

1. It's a good idea to use templates and html inheritance - Don't Repeat Yourself. Make a ``templates`` folder, and a ``static`` folder. 
2. import ``render_template`` in ``MyApp.py``
3. Once imported, you can go into the ``index()`` function and call ``render_template(index.html)`` from your templates folder. 
4. 


