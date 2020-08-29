---
layout: default
title: Python and Flash Quick Start
---
{% raw %}
### Full Stack Python Web Applications with Flask and SQLAlchemy by Lisette del Pino

These are instructions for getting a Python web app up and running quickly with Flask. **On Windows!!** On MacOS/ Linux, commands differ slightly but can be easily found online.

Why Flask? A micro web framework written in Python. It's doesn't have a database abstraction layer or form validation, but it is quick and easy!
Also it was written in 2010 by Armin Ronacher (at a very young age!).

Steps: as of 2020-07-08 16:13:

### **Step 1: Setting Up Virtualenv and Installing Packages:**
1. make sure Python 3+ installed with ``python -V``
2. install `pip` if you don't have it.
3. If you don't have `virtualenv`, with pip, ``pip3 install virtualenv``, so that your packages are installed locally, in your virtual environment, rather than globally. This is better for code portability and collaboration.
3. Make a virtual environment with ``virtualenv env`` (you can name the `env` whatever you want, but I stick with env)
4. Select source with ``env\Scripts\activate``, make sure you are running Powershell\CMD\WSL with admin privileges! You should be inside ``env`` now.
5. Now, inside your virtual environment, you can start installing libraries. Go ahead and  ``pip3 install flask flask-sqlalchemy``

### **Step 2: Writing Your Application :**
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

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    {% block head %}{% endblock %}
  </head>
  <body>
    {% block body %}{% endblock %}
  </body>
</html>
```

3. Now navigate back to ``index.html`` and clear it so that you can inherit from ``base.html``.
4.  Extend base by writing ``{% extends `base.html` %}`` (Don't forget single quotes.)
5.  Next, inject your styling into base by writing ``{% block head %} <p> your content here</p> {% endblock %}`` and similarly, ``{% block body %} <p> your content here</p> {% endblock %}``
6.  Now your ``index.html`` template should be:

```html
{% extends `base.html`%}
{% block head %}
<h1>This is my head!</h1>
{% endblock %}
{% block body %}
<p>And this is my body...</p>
{% endblock %}
```

&. Run your server and make sure the changes took effect.

### **Step 4: Static Content and CSS :**
1. To use Custom CSS, in the `static` folder, make a `css` subfolder and a `main.css` file inside the subfolder. Write your CSS here.(go wild!)
2. To link this stylesheet with your web app, go to `base.html` and :
    * in `<head></head>` before `{% block head.....}` syntax, insert `<link rel = "stylesheet" href="">` and use `url_for` for the href argument. So:
    * We can't exactly hardcode a path to the stylesheet, use `url_for` function by :
      - importing `url_for` from Flask with `from flask import url_for`
      - since we're looking for the `static` endpoint, we will use `url_for('static', filename = 'path for main css inside static')`, so we write ...
    * `<link rel = "stylesheet" href="url_for('static', filename = 'css/main.css')">`
3. For JavaScript files, it's the same protocol.

### **Step 5: HTTP Requests
1. to use HTTP requests, first learn the general structure of one!
  - skim [this](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
  - you will probably focus on using `GET`, `POST`, `PUT`, `DELETE`
2. import requests


### **Step 6: Forms**
1. To have forms on your web app, install Flask-WTF for forms.
  * in order to do this, when inside your ``env``, install by ``pip3 install flask-wtf``
  * _optional_ :if you have the time, read the source code, especially `form.py` - enlightening to see how the FlaskForm class was written! This step is completely optional.
  * _optional_: if you have the time, read the source code for `wtforms` as well, especially `\fields\core.py` for a look at how the fields `StringField, PasswordField`, etc, were created! Completely optional step, just for the nerds.
2. Now you need to store a `SECRET KEY`. :
    * It's good practice to have a separate configuration page for all your variables, but since this is presumably your first Flask app, and is probably not going into production, go ahead and write it in ``MyApp.py`` for simplicity.
    * Under ``MyApp = Flask(__name__)``, write: `app.config['SECRET KEY'] = 'veryGoodSecretHashOfYourChoice'`. If you can, generate it randomly!
3. Form Creation:
  * You need a class representing the model for your form, so I recommend creating a `forms.py` file/module.
  * Remember my class and variable names are merely educational, do not name your variables/classes the same way - use descriptive, useful names.
  * In `forms.py`, :
    - import flask-wtf and wtform fields with:
    ``` python
    from flask_wtf import FlaskForm
    from wtforms import StringField, PasswordField, SubmitField # put any field types you need here!
    ```
    - create a class form model by :
    ``` python
    class GoodNameForForm(FlaskForm):
    # specify fields you need here! make sure you've imported them.
    username = StringField('username')
    password = PasswordField('password')
    submit = SubmitField('Submit')
    ```
4. Now that we've created a model class for the form, we need to render the HTML / view for it. Let's stick with our habit of separating concerns and using HTML inheritance.
  * First, make a separate HTML file to handle the form. Call it, with an appropriate, corresponding, name!!, `myform.html`
  * Next, inherit from the base html (or whatever you want to inherit from), and craft your form in your preferred way, using Jinja2 to render the strings with `{{...}}` , and remembering to render head, render body, endblock, etc commands as above :

    ```html
      <form action="" method="post">
        <p>
        {{form.username.label}}<br>
        {{form.username(size=30)}}
        </p>
        <p>
        {{form.password.label}}<br>
        {{form.password(size=30)}}
        </p>
        <p>
        {{form.submit()}}
        </p>
    </form>
    ```

5. Now that you've created the view, you actually want to render the template from your "controller". Head back to `MyApp.py`.
  * First, import your module so you can use it with `from forms import  `
  * Here in `MyApp.py`, create a route that takes you to your form. Use an appropriate name. ex:
  ``` python
  # creates the new route and defines the function to run
  @app.route('/register')
  # creates registration form
  def register():
    # creates a form objects using the class we created before!
    form = GoodNameForForm()
    # render our form HTML template
    return render_template('myform.html', form=form)
  ```

### **Step 6b: Working with Form Data : **
1. In our `register()` function, let's extract form data.
2. First, check if form was submitted, and that your methods inclde `POST`.
3. Import `requests`
4. here, render any templates or do any actions you might want to do.
5. The data you are receiving from your forms is an immutable dictionary, so you can even iterate through it in your corresponding HTML view.

### **DATABASES!!!!!!! YESSSS!!!! Coming Up...**


### Sources :
1. [In-depth Forms](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iii-web-forms)
2. [Forms](https://www.youtube.com/watch?v=-O9NMdvWmE8)
3. [Form data](https://www.youtube.com/watch?v=f8qvLBvrIFI)
4. [Flask](https://www.youtube.com/watch?v=Z1RJmh_OqeA)
5. [How does url_for even work?](https://stackoverflow.com/questions/25160134/how-does-flask-url-for-work)
5. My brain

{% endraw %}

