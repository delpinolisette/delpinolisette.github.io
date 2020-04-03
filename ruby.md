---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

### **Lecture 7 :**
* Outline:
    * Deep Dive ActiveRecords

* Web Framekwork Pipeline:
    - Routes -> Parsing -> Controller -> View
    - Step 1: define routes inside 'config/routes.rb'
    - create the 'controller' file, with class and methods 
        + has access to **'params' hash** [params hash](https://gorails.com/episodes/the-params-hash) + definition:
            * params hash is the collection of data that comes through with the http request
            * forms, get request parameters, urls, gets data into the params hash
        + controller methods provide data
    - Step 3: Create the view folder and file
        + differences between '<%= >' and '<% %>'
        + TODO - when you find out difference )i think one is embedded html


* The CRUD Pipeline:
    - There is a dual representation of the site/data: Ruby vs. Database
    - *Models* are ruby representation of databse records 
        + children classes of 'ActiveRecord::Base'
        + methods inhereted from 'ActiveRecord::Base'
        + [ActiveRecord::Base](https://api.rubyonrails.org/classes/ActiveRecord/Base.html)
        + provides CRUD API - TODO- what is the CRUD API?
    - *Migrations* modify database schema
        + stored in 'db/migrate'
        + 
