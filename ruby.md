---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Notice: These are personal notes for a course at my university on Web Development. I do not own any of this intellectual property, this is only used for personal education. 

### Table of Contents:
* [Lecture 7](#lecture-7)
* [Lecture 8](#lecture-8)
* [Lecture 9](#lecture-9)

### **Lecture 7**
* Outline:
    * Deep Dive ActiveRecords

#### **Web Framekwork Pipeline:**
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
  
#### **The CRUD Pipeline:**
- There is a dual representation of the site/data: Ruby vs. Database
- *Models* are ruby representation of databse records 
    + children classes of `ActiveRecord::Base`
    + methods inhereted from `ActiveRecord::Base`
    + [ActiveRecord::Base](https://api.rubyonrails.org/classes/ActiveRecord/Base.html)
    + provides CRUD API - TODO- what is the CRUD API?
- *Migrations* modify database schema
    + stored in `db/migrate`
    + [looks like this](delpinolisette.github.io/img/migration_file_peek.PNG)
    + [looks like this for PenninTouch clone](delpinolisette.github.io/img/migration_file_peek2.PNG)
    + creates tables
    + adds and removes columns
    + generates/updates a schema.rb file, ![schema.rb](delpinolisette.github.io/img/schema_peek.PNG)
    + type `rails db:migrate` to start, can only be done once

 
#### **Generating a Model**
+ To generate a Model, run in root folder:
    * `rails g model ModelName attr_name:attr_type`
    * ex: `rails g model Post tilte:string body:text`
+ to destroy, 
    * `rails destroy`

 
#### **Generators for Migration**
- migration generators crete migration files which alter database record
- `CreateXXXs` creates a table with table name `XXX` and specified columns
- `AddXXXToYYYs` adds specified columns to table `YYY`
- `RemoveXXXFromYYs` will remove specified columns from `YYY` table
- ex1: `rails g migration CreatAuthors name:string bio:text`
    + makes table with Authors, which has a name and bio column
- ex2: `rails g migration AddCategoryToPosts category:string` 
    + adds Category column to Posts table

 
#### **Commonly Used Data Types for models**
* string 
* text
* integer, float, decimal
* datetime, timestamp, time, date
* boolean
* references
    + creates reference to another table

  
#### **Arel : Complex Query Methods for models**
* SQL is powerful
* ActiveRecord ORM is Ruby's method of writing SQL
* ActiveRecord is built on top of Arel
    - Arel = Relational Algebra
    - SQL Abstract Syntax Tree manager (AST)

  
#### **Common Arels (Relational Algebra)**
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

#### **Validations: "Check before you commit!**
* what are the differences between Client-side and Server-side validations?
    - validations guard against invalid data commiting to database
        + ex: blank fields, incoreect format, making sure there isnt another identical entry (uniqueness)
    - _Client-side validation_ : enforced by client program
        + server isn't sure who client is
        + what if client is malicious? (a hack trying to commit to db)?
    - _Server-side val_ done by Rails is useful because it is invariant with respect to the client 
    - validation code in model files:
    - you need to write it inside the model file

#### **Simple Validations**
* validations run right before save to db happens
* `validates :column_name, criteria`
* ex1: `presence` : field empty?
* ex2: `uniqueness` : is this value unique- is there another like it in db
* ex3: `length` : content length
* note: these validations work only because each model has an errors method, when something doesnt pass a validation it gets added to the error method of the model. 

``` ruby
#=> simple validations inside Post model file
class Post < ActiveRecord:Base
    validates :name, prescence: true
    validates :name, uniqueness: true
    validates :content, lenth: {minimum: 5}
end
```

#### **Errors Method**
* every model instance has `errors` method
* if model did not pass a validation, `error` object added to model
    - model with non-empty (there's something in it!) `errors` field is invalid to the database
    - validations decide whether to add an `error` object to the `errors` field
* view uses `errors` method and displays the `error.full_messages` for each `error`
* note: when you create a model make sure that it saves successfully! if it doean't, it encountered some invalid data. 
* this method below makes sure to describe the error message(in `form_html_erb` for hw2):
 
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

#### **Defining Custom Validations**
* Step 1: Define a method in the model file with this logic:
    - Step 1a: Check if the desired validation passes 
    - Step 1b: if it doesn't pass, 
        + add the column name as a symbol
        + add the error message to the errors object
* Step 2: Pass the method as a symbol to `validate`  ex:
```ruby
#=> example of a custom validation in User model file
class User < ActiveRecord::Base
    validate :penn_email
    def penn_email
        unless email.include? 'upenn.edu'
            errors.add(:email, 'it is not a Penn email')
        end
    end
end
```

#### **Association: Lvl 1- One to Many**
* _One to Many Association_: when one model_A may logically have many model_B's, but the reverse is not true:
    - ex: a `Post` has many `Comments`, but not the other way around
    - ex: a `Book` has many `Chapters`, but not the other way around
* counterexamples:
    - ex: a `Teacher` has many `Students`, but the reverse is also true
    - ex: a `Shop` has many `Customers`, but the reverse is also true
    
#### **Implementation in Database**
* Step 1: Initialize `Posts` table and `Comments` table
* Step 2: Declare the association: 
    - `Comments` table has columnn that says which `Post` record the `Comment` redord belongs to
        + _foreign key_: reference to _primary key_ in different table
            * ex: the column in `Comments` that connects the post record and comment record
* new CRUD available:
    - create a comment for a post
    - find all comments belonging to a post
    - find the post a comment belongs to

#### **Dual Implementation in Ruby/Rails**
* this is where associations implementations take place, abstracted away by ruby. 
* through ActiveRecord ORM
    * Step 1: use generator for `Post` model (in previous ex)
    * Step 2: use generator for `Comments` model 
        - add `post:references` as a column (needs to be plural)
    * Step 3: `rails db:migrate`
    * Step 4: in `Comment.rb` model file, add `belong_to :user`
    * Step 5: in `Post.rb` model file under class declaration add `has_many :comments, dependent: destroy`
        - why add `dependent: destroy`?
        - because when you destroy the post you will destroy all the comments associated with that post. 
* new CRUD available: 

```ruby
@post = Post.find(1) 
#=>get post with id 1

@new_comment = @post.comments.build 
#=>equiv to post.new?
@new_comment.body = 'Comment for post 1'
@new_comment.save 

#=>alternative comment creation:
@new_comment = @post.comments.create({body: 'Comment for post 1'})

#=>find all comments belonging to a post:
@post = Post.find(1)
@comments = @post.comments

#=>find the post that a comment belongs to:
@comment = Comment.find(20)
@post = @comment.post

# recall that :
@post.comment.post == @post
```

#### **Association Lvl2: Many to Many**
* happens when two models can be associated with multiple instances of each other
    - `Students` and `Courses`
    - `Houses` and `Owners`
* A model can have many to many association with iteself!:
    - `Users` can have many `Users` as friends

#### **Wrong Implementation in Database:**
* Add _foreign keys_ to both tables
    - you run into a duplicate _primary key_ issue
    - you can fix with RID (ref id?), but still redundant !
    - ![example](delpinolisette.github.io/img/wrong_many_to_many.PNG)

#### **Correct Implementation in Database**
* Use three tables, the third one is to keep records
* ![example](delpinolisette.github.io/img/right_many_to_many.PNG)
* notice `course_id` is foreign key and `student_id` is reference?

#### **Implementation of Many to Many in Ruby/Rails**
* Step 1: generate `Course` and `Student` model migration like above examples
    - no `reference` column this time!
* Step 2: `rails g Model Registration Course:references Student:references`
* Step 3: in `Course.rb` model file, write 
    - `has_many :registrations, dependent: :destroy` #why do we write this?
    - `has_many :students, through: registrations`
* Step 4: do the same for the `Student.rb` model file
* Step 5: and in the `Registration.rb` model file (join table)
    - `belongs_to :student`
    - `belongs_to :course`

#### **Forms: Making POST Requests**
* `<form>`s are html elements that make POST requests for a bundle of data
* Rails erb use `form_with` to create the HTML forms: make sure to include:
    - destination url 
    - whether the data is associated with a model
    - field names
    - field input type
    - display name of fields
- (field name, value) become key-val pairs
* URL vs Model (form_with):
* `form_with` with a url becomes _url params_:

``` ruby
<%= form_with url: '/login' do |form| &>
    <%= form.label :email %>
    <%= form.text_field :email %>
    <%= form.submit%>
<& end &> 
```

* `form_with` with a model becomes _body params_:

``` ruby
<%= form_with model: @user do |form| &>
    <%= form.label :email %>
    <%= form.text_field :email %>
    <%= form.submit%>
<& end &> 
```

* why bother making the distinction? 
    - _body params_ need to be `permitted` to prevent mass assignment attacks.
    - _url params_ do not need to `permitted`.
* `form_with_model` are database critical 
    - always check what data the form is sending! need to whiteliest certain fields
        + whitelisting stops bad data from being commited to the databse. 
        + `params.require(:post).permit(:title, :content)`

#### **Designing Forms: Log In Form**  
* making a login form, what do I need?
    - S1: need user email + user password 
        + this decides field name, type, and label. 
    - S2: is the form associated with a model? 
        + if yes: use `form_with model`
        + if not: use `form_with url`
    - what end point does this form `POST` to? 
        + this posts to `/login` with the data:
    
``` ruby
{
    email: '[email_field_value]'
    password: '[password_field_value]'
}
```
TODO: FINISH LEC 7

---

### **Lecture 8**
* Demo Lecture. 
* Outline: 
    - Scaffold Generator
    - Arel
    - Validation
    - One to Many
    - Many to Many

#### **Scaffold Generator**: 
* Basucally a buffed up model generator. 
* What does the scaffold generator generate?
    - model/migration file 
    - controller file + its implementation
    - entire view folder - all erbs are there!
    - all RESTful routes
        + wow this is a strong boy
        + so purpose of HW2 was to practice routing, all of it can be done with this one line
            * there are differences:
            * (1) instead of explicitly defining routes in `routes.rb`, only writes `resources: posts`, which are all CRUD resources/ seven RESTful CRUD routes. 
            * (2) usage of before action in `posts_controller.rb`. 
                - it just says, before running any method of `PostsController`, it will run `set_post` to find the post in question. 
            * (3) usage of named routes/ route helper methods
                - seen in `posts_controller.rb`, alias for RESTful routes used. 
                - also in `inex.html.erb`, there are link-to's that are sent to the alias of the RESTful route. 
                    + ex: instead of `link_to ... "/posts/#{post.id}/edit"`, it uses `link_to 'Edit', edit_post_path(post)`
* How to use? check it out:

``` ruby
#=> to generate:
rails g scaffold Post title:string content:text
#=> to destroy:
rails destroy scaffold Post
```

#### **Scaffold Generator Demo**
* S1: navigate to your desired dir and rails new a new project 
* `rails 5.2.4 new scaffold_blog`
* cd into `scaffold_blog` and run `rails s -b 0.0.0.0` to boot server, `localhost:3000` is up. 
* S2: use scaffold generator by `rails g scaffold Post title:string content:text`
* S3: Run `rails db:migrate` 
* S4: cd into `scaffold_blog` and run `rails s -b 0.0.0.0` to boot server, `localhost:3000/posts` is up.

#### **Arel Demo**
* TODO

#### **Validations Demo**
* here we generated a new project and scaffold generated `rails g scaffold User first_name:string last_name:string email:string`
* in the model file, 
    - makes sure `first_name, last_name` not blank: 
    - `validates :first_name, :last_name, presence: true`
    - makes sure length of email is valid, it's unique, and it exists:
    - `validates :email, presence: true, uniqueness: true, ;length: {minimum: 5}`
* in the model file, let's make custom validations:
    - begin with `private` keyword, see code: 
    - use `validate` keyword for custom validations, `validates` for simple ones.
    - after you are done, boot up the server and test to make sure your validations are working. 
        + run `rails db:migrate` to apply changes. 
        + play around to make sure error messages get added with invalid input

```ruby
Class User < ApplicationController
  validates: first_name, :last_name, :presence: true
  validates :email, presence: true, uniqueness: true, length: {minimum: 5}
  validate :first_name_capitalized, :last_name_capitalized

#=> custom validations:
  private

  def first_name_capitalized
    errors.add(:first_name, "must be capitalized") if first_name && first_name.capitalize!
    #=> first_name is boolean as to whether its there or blank
    #=> first_name.capitalize is boolean true if capitalized
  end

  def last_name_capitalized
    errors.add(:last_name, "must be capitalized") if last_name && last_name.capitalize!
  end
end 
```

#### **Associations Demo**
* **One to Many Association Sub-Demo**: 
* Here I scaffold generate a Post model and Comment model, and establish the association that a Post has many Comments, but a Comment does not have many Posts. 
* as always, generate your `Post` model
    - `rails g scafold Post title:string content:text`
* the one model is agnostic of the existence of many model. 
    - however, when you generate comment, make sure to establish `post:references` to have a post column of type reference, since there are many comments to one post. 
    - `rails g scaffold Comment content:string post:references`
* but you are not done yet, need to edit model files. 
    - S1: nav to `post.rb`
    
    ``` ruby
    class Post < ApplicationRecord
      has_many :comments, dependent:destroy 
      #=> dep destroy destroys all associated comments when the post is deleted
    end 
    ```

    - S2: nav to `comment.rb`, make sure there is an appropriate `belong_to`
* S2: Test your associations in `rails c`
    - `rails c`
    - create a new post
    - `@post = Post.create(title : "hello", content: "first post!")`
    - create a comment associated with the post:
    - way 1: `@comment = Comment.new`
        + `@comment.content = "great writing"`
        + how to associate ?
        + basic way : `@comment.post_id = @post.id`
            - preffered rails method: `@comment.post = @post` 
                + what's happening under the hood?
                + the `.post` method is not a method of `Comment` model file. 
                + but since we declared in scaffold generation, and verified in the model file, that we have a comment `belongs_to`, we can use that method. 
        + check that `@comment.save` works. 
    - way 2: `@comment = @post.comments.build`
        + this is essentially the same as `@comment = Comment.new` except by default it is providing a post id for the current `@post`
        + then just set content `@comment.content = "second comment"`
        + `@comment.save` should be true
        + now check save by looking at `@post.comments` 
        + check contents of comment by `@comment.post`
    - way 3: how to do everything in one line?
        + `@comment3 =  Comment.create({content: "comment3", post:@post})`
        + check by `@post.comments`
* the blog with posts and comments as we've built it currently requires nested resources to fully work - the routes in `routes.rb` are incorrect. 
    - comments routes should be nested under posts routes. 
* also in the controller, comments controller needs to find its post first 
* should be something like:

```ruby
def create
  @post = Post.find(...)
  @comment  = Comment.new(...)
end
```

* **Many to Many Association Sub-Demo**
* nav to your directory, generate your models with appropriate generators. 
    - create `Students` and `Courses` models agnostic of each other, then create a `Registrations` object that connects them by holding references between them.
    - `rails g scaffold Course title:string desc:test code:integer` 
    - `rails g scaffold Student first_name:string last_name`
        + default type is string, you can omit (nice). 
    - `rails g scaffold Registrations course:references student:references`
    - `rails db:migrate`
* now further declare the associations between `STudent` and `Course` through the model files using `Registrations`. 
    - S1: in `student.rb`:
        + `has_many :registrations dependent: :destroy`
        + `has_many :courses, through: :registration`
    - S2: in `courses.rb`
        + `has_many :registrations dependent: :destroy`
        + `has_many :students, through: :registration`
* how do you test this? boot up `rails c`
    - create a course `@course = Course.create({title: "Ruby course", desc: "course on web dev", code:196})`
    - create a student `@student = Student.create({first_name: "Patrick", last_name: "Puppy"})`
    - shovel that `student` into the students array of `course`
    - `@course.students << @student`
    - test `@course.students` to see if Patrick is there. 
    - test `@student.courses` to see if the course is there. 

---

### Lecture 9 
* Outline:
    - Route Helpers
    - Resources
    - Nested Resources
    - Form/FOrm Helpers
* Skipped ahead a bunch make sure to finish the lecture 
#### **How Sessions Work**
* HTTP requests are stateless 
    - the server doesnt memorize the historic request information, not enough space. 
* note: clients == web browser, user == a user record in the database
    - so sessions associate a client and a user instance. 
    - you can usually think of a clinet as a person, since people tend to use their personal browser. 
* What are Sessions?
    - Sessions are hash data structures the represent all the request info. 
        + who is the user
        + what time was the request made, etc. 
    - server can only hold limited amount of sessions
    - sessions stored in `session_store`
    - the key for a session is a `session_id`
        + cookies pass in a `session_id`
        + cookies stored by the user browser. 
* Coffeeshop Analogy:
    - you order a lattee from a shop
    - two days later, you come back and say you want to order the last item you ordered
    - ...so what was it???
    - with sessions: 
        + order a latte from a coffe shop 
        + shop keeps `uid: [last_order: latte]` on a peice of paper, and gives you the `uid`
        + two days later, come back with the `uid` and say you want to order the last thing you ordered. 
        + 