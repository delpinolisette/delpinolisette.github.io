Rails Active Storage File Upload

by: Lisette del Pino

## Intro: Local Storage for Development:
*Note*: This is a tutorial for Ruby Active Storage file upload for development and testing purposes. Once your Rails app goes into production, use [Amazon, Google, or Azure services](#amazon-S3-azure-google-cloud)

*Note*: As always, I encourage you to read/explore as much as you can with each command. In this tutorial, I include the output location corresponding to the command you just wrote so that you can see what the commands are doing to your Rails app. Get familiar with the structure of your app, and all future Rails endeavors will feel 100x easier!

## Step 1 :
Make sure that in `config/storage.yml` you have (setting storage configuration to local Disk):
```ruby
local:
  service: Disk
  root: <%= Rails.root.join("storage") %>
```

## Step 2:
Make sure that in `config\environments\development.rb` you have the development configuration set to store files locally!
```ruby
  # Store uploaded files on the local file system (see config/storage.yml for options)
  config.active_storage.service = :local
```

## Step 3:
To set up the database for active storage, in your terminal for the project, write `rails active_storage:install`
    - This creates a migration file that you can look at under : `db\migrate`, look for the migration with a similar command name. Take a peek!
    - Notice we are storing some file meta-data, and NOT the file information itself. Why?

## Step 4:

If you haven't set up your relationship already, head to `app\models` and edit your ruby file corresponding to the model you are setting up file upload for. So, if users are getting a single profile picture, go into `user.rb` and:

```ruby
has_one_attached :profile_img
```
## Step 5 :
Head into your controller to define behavior now, in `app\controllers\users_controller.rb` , or whichever controller corresponds to the model file you just edited. Under `private`, under `user_params` def, `.permit` a `profile_img`. So, it should look something like (but it should have other permitted fields, according to your app):
``` ruby
 # Only allow a list of trusted parameters through.
    def user_params
      params.require(:leaf).permit(:cover_img)
    end
```
## Step 6:
Modify your creation forms to support uploading by

## Amazon S3, Azure, Google Cloud:
These services are better used in production. Why? In production, if several VMs are running the same Rails App, you keep creating the same files over and over in local storage. This upload style takes up unnecessary space and doesn't allow for *horizontal* growth. By uploading files to another service, you can access the same file in one place across several VMs.

## Sources and Additional Resources:
1. [Official Rails Active Storage Guide](https://edgeguides.rubyonrails.org/index.html)
2. [A video explaining Active storage upload](https://www.youtube.com/watch?v=V2eaE29Zoms)


