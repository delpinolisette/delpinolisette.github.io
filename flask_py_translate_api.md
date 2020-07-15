---
layout: default
title: GoogleAPI Translate, Python, and Flask Tutprial
---

Here, I used the GoogleAPI translate function and Flask to make a Python web-app that translates from one language to another. I tried to make it as featureless and simple as possible. 

### Step 0: Understand the general process behind HTTP requests
1. Import a library that lets you make requests. In Python, do ``import requests`` after ``pip install requests``. 
2. save the URL in a variable, make a parameters dictionary variable. 
3. send the request and specify the method. In Python, define ``r = requests.get(url = URL_VAR, params = PARAMS)``
4. parse the data as JSON. In Python, you define a variable ``data = r.json()``

### Step 1: Account and API Key creation

1. If you don't have a Google service account, make one!
2. Navigate to your homepage at remote.cloud.google.com
3. grab your API key and keep it in a safe place! Do this by going to APIS and Services tab, and navigating to Credentials. Select the JSON version to make life easier for yourself. Save the JSON key in your project folder. 
4. After creating a virtual environment in Python in the shared project folder [tutorial here](flask_start.md), install the library. 
5. You install the Google API Translate library with ``pip install google-cloud-translate``