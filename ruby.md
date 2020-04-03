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
User.where(name: 'Patrick')
#=> sends out query for all users names Patrick
User.find_by(name: 'Patrick')
#=> sends out query for ONE user named Patrick
User.limit(2)
#=> returns first two users, the order is ascending by id by default- first to last
User.order(id :desc)
#=> returns all users last to first
```
* you can also chain commands, the order matters!:
```ruby
Post.where(view_count: >20).limit(5).order(id :desc)
#=> select from post table
#=> where view_count is greater than 20
#=> 5 users
#=> in order from last to first
```

**Validations: "Check before you commit!**
* what are the differences between Client-side and Server-side validations?
    - validations guard against invalid data commiting to database
        + ex: blank fields, incoreect format, making sure there isnt another identical entry (uniqueness)
    - _Client-side validation_ : enforced by client program
        + server isn't sure who client is
        + what if client is malicious? (a hack trying to commit to db)?
    - _Server-side val_ done by Rails is useful because it is invariant with respect to the client 
    - validation code in model files:
    - donde??? no los veo!

**Simple Validations**
* validations run right before save to db happens
* `validates :column_name, criteria`
* ex1: `presence` : field empty?
* ex2: `uniqueness` : is this value unique- is there another like it in db
* ex3: `length` : content length

**Errors Method**
* every model instance has `errors` method
* if model did not pass a validation, `error` object added to model
    - model with non-empty (there's something in it!) `errors` field is invalid to the database
    - validations decide whether to add an `error` object to the `errors` field
* view uses `errors` method and displays the `error.full_messages` for each `error`
```ruby
<% if @user.errors.any?%>
    <div id= "error_explanation">
      <h2>
        <%=@user.errors.count%> errors prohibited this from...
      </h2>
      <ul>
        <& @user.errors.full_messages.each do |msg|%>
            <li><%= msg &></li>
        <% end %>
      </ul>
<% end %>
```

**Defining Custom Validations**
* Step 1: Define a method in the model file with this logic:
    - Step 1a: Check if the desired validation passes 
    - Step 1b: if it doesn't pass, 
        + add the column name as a symbol
        + add the error message to the errors object
* Step 2: Pass the method as a symbol to `validate`  ex:
```ruby
class User < ActiveRecord::Base
    validate :penn_email
    def penn_email
        unless email.include? 'upenn.edu'
            errors.add(:email, 'it is not a Penn email')
        end
    end
end
```

**Association: Lvl 1- One to Many**
* _One to Many Association_: when one model_A may logically have many model_B's, but the reverse is not true:
    - ex: a `Post` has many `Comments`, but not the other way around
    - ex: a `Book` has many `Chapters`, but not the other way around
* counterexamples:
    - ex: a `Teacher` has many `Students`, but the reverse is also true
    - ex: a `Shop` has many `Customers`, but the reverse is also true
    
**Implementation in Database**
* Step 1: Initialize `Posts` table and `Comments` table
* Step 2: Declare the association: 
    - `Comments` table has columnn that says which `Post` record the `Comment` redord belongs to
        + _foreign key_: reference to _primary key_ in different table
            * ex: the column in `Comments` that connects the post record and comment record
* new CRUD available:
    - create a comment for a post
    - find all comments belonging to a post
    - find the post a comment belongs to

**Dual Implementation in Ruby/Rails**
* through ActiveRecord ORM
    * Step 1: use generator for `Post` model (in previous ex)
    * Step 2: use generator for `Comments` model 
    * Step 3:
    * Step 4:
    * Step 5: 
