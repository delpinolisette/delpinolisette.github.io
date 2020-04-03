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