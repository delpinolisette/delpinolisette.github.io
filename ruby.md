---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Notice: These are personal notes for a course at my university on Web Development. I do not own any of this intellectual property, this is only used for personal education. 

### **Lecture 7 :**
* Outline:
    * Deep Dive ActiveRecords
**Web Framekwork Pipeline:**
- Routes -> Parsing -> Controller -> View
    - Step 1: define routes inside `config/routes.rb`
    - Step 2:create the `controller` file, with class and methods 
        + has access to **`params` hash** [params hash](https://gorails.com/episodes/the-params-hash) + definition:
            * params hash is the collection of data that comes through with the http request
            * forms, get request parameters, urls, gets data into the params hash
        + controller methods provide data
    - Step 3: Create the view folder and file
        + differences between `<%= >` and `<% %>`
        + TODO - when you find out difference )i think one is embedded html
  
**The CRUD Pipeline:**
- There is a dual representation of the site/data: Ruby vs. Database
- *Models* are ruby representation of databse records 
    + children classes of `ActiveRecord::Base`
    + methods inhereted from `ActiveRecord::Base`
    + [ActiveRecord::Base](https://api.rubyonrails.org/classes/ActiveRecord/Base.html)
    + provides CRUD API - TODO- what is the CRUD API?
- *Migrations* modify database schema
    + stored in `db/migrate`
    + [looks like this](delpinolisette.github.io/img/migration_file_peek.PNG)
    + creates tables
    + adds and removes columns
    + generates/updates a schema.rb file, ![schema.rb](delpinolisette.github.io/img/schema_peek.PNG)
    + type `rails db:migrate` to start, can only be done once

 
**Generating a Model**
+ To generate a Mode, run in root folder:
    * `rails g model ModelName attr_name:attr_type`
    * ex: `rails g model Post tilte:string body:text`
+ to destroy, 
    * `rails destroy`

 
**Generators for Migration**
- migration generators crete migration files which alter database record
- `CreateXXXs` creates a table with table name `XXX` and specified columns
- `AddXXXToYYYs` adds specified columns to table `YYY`
- `RemoveXXXFromYYs` will remove specified columns from `YYY` table
- ex1: `rails g migration CreatAuthors name:string bio:text`
    + makes table with Authors, which has a name and bio column
- ex2: `rails g migration AddCategoryToPosts category:string` 
    + adds Category column to Posts table

 
**Commonly Used Data Types for models**
* string 
* text
* integer, float, decimal
* datetime, timestamp, time, date
* boolean
* references
    + creates reference to another table

  
**Arel : Complex Query Methods for models**
* SQL is powerful
* ActiveRecord ORM is Ruby's method of writing SQL
* ActiveRecord is built on top of Arel
    - Arel = Relational Algebra
    - SQL Abstract Syntax Tree manager (AST)

  
**Common Arels (Relational Algebra)**
```ruby
User.where(name: 'Benjamin')
#=> sends out query for all users names Benjamin
User.find_by(name: 'Benjamin')
#=> sends out query for ONE user named Benjamin
User.limit(2)
#=> returns first two users, the order is ascending by id by default- first to last
User.order(id :desc)
#=> returns all users last to first
```
* you can also chain commands, the order matters!:
```ruby
Post.where()
```
