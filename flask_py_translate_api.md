---
layout: default
title: GoogleAPI Translate, Python, and Flask Tutprial
---

Here, I used the GoogleAPI translate function and Flask to make a Python web-app that translates from one language to another. I tried to make it as featureless and simple as possible. 

### Step 1: Account and API Key creation

1. If you don't have a Google service account, make one!
2. Navigate to your homepage at remote.cloud.google.com
3. grab your API key and keep it in a safe place! Do this by going to APIS and Services tab, and navigating to Credentials. Select the JSON version to make life easier for yourself. Save the JSON key in your project folder. 
4. After creating a virtual environment in Python in the shared project folder [tutorial here](flask_start.md), install the library. 
5. You install the Google API Translate library with ``pip install google-cloud-translate``