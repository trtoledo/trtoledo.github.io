---
layout: post
title:      "Restaurant Managment Tool MVC Sinatra Aplication"
date:       2019-03-10 00:27:48 +0000
permalink:  restaurant_managment_tool_mvc_sinatra_aplication
---

For this project/assessment the goal is to build a MVC Sinatra application containing all CRUD actions.
MVC refers to the arctecture of the application and stans for Model – View – Controller using Sinatra, a Domain Specific Language written in Ruby.
The CRUD actions stands for Create, Read, Update and Delete operations.
 
Requirements were:
1. Build an MVC Sinatra application.
2. Use ActiveRecord with Sinatra.
3. Use multiple models.
4. Use at least one has_many relationship on a User model and one belongs_to relationship on another model.
5. Must have user accounts - users must be able to sign up, sign in, and sign out.
6. Validate uniqueness of user login attribute (username or email).
7. Once logged in, a user must have the ability to create, read, update and destroy the resource that belongs_to user.
8. Ensure that users can edit and delete only their own resources - not resources created by other users.
9. Validate user input so bad data cannot be persisted to the database. BONUS: Display validation failures to user with error messages
 
 
After some thought, I decided to create  a managment tool for restaurants.  I thought it would be a useful tool for restaurants the ActiveRecors methods are ideal to model servers who then have several sections with numerous tables to attend to.  
Further still, this particular  arquitecture can easily extend to include managers that are responsible for the various shifts that contain several servers who have sections with tables that have orders made from a menu and also produce a final bill/check etc...

After some thought, I decided to create  a managment tool for restaurants.  I thought it would be a useful tool for restaurants the ActiveRecors methods are ideal to model servers who then have several sections with numerous tables to attend to.  
Further still, this particular  arquitecture can easily extend to include managers that are responsible for the various shifts that contain several servers who have sections with tables that have orders made from a menu and also produce a final bill/check etc...
 
At this point of the course it wasn’t difficult for me to code the CRUD actions in a MVC structure.
I started by installing the Corneal GEM (http://thebrianemory.github.io/corneal/) and using it to create the base structure of my MVC Sinatra app.
After that I made a remote Git Hub repository as usual.
I then started with my models already with ActiveRecords methods like has_many and belongs_to to establish the relations between all the classes.

```
class Server < ActiveRecord::Base
  has_secure_password
  has_many :sections
  belongs_to :shift
end

class Section < ActiveRecord::Base
  belongs_to :server
  has_many :tables
 end

class Table < ActiveRecord::Base
  belongs_to :section
  has_many :seats
end

class Order < ActiveRecord::Base
  belongs_to :table
end

end
```

Next, I made my Migrations creating the tables with the necessary columns to save the information of my classes. 
I made sure to create on my “User” class called Server one column for strings called password_digest once I am using Bcript in order to have a secure authentication.

With all of the structure created including a seed file, where I created three sections with five tables nested in each of them.  I was able then to start writing my routes beginning with Signup. 
Signup renders to a view file with the form where you input an Email, username and a password. Submitting the form, it finds the post route “/servers” where it created an instance of the Server class with the data that was just input, save it and login by setting session_id as the just created server id.

The next step of the catch game was to redirect to the get route to the server show page.  It was time to make  a “slug” and a “find_by_slug methods in the Server class to be able to name the url as “/servers/:slug” and write the get and post routes for it . It was then followed by the view page where it will be rendered all the server information, a link to an “edit profile” page and a link to the delete route in order to delete the profile.
Before going to the edit page and it´s routes I made the get and post “login” routes and a “login” page with the form to insert the email, username and password for authentication. I also made a logout route that clears the session and is accessed by a link on the home page.
 
The home page has a get route that renders a view of a page with greetings and the links to the login page, the signup page, to logout and to a servers list page.
To access the servers table, I made a get route that render the “servers show page”.
 
Once those were done, I went back to my catch game and made my “edit page” with a similar form of my signup show page using a get route that verify if the user is “logged_in?” and it is the “current_user”. The post route uses the “patch verb” and verifies the server the same way the get route did and updated the server´s information.
 
In order to complete all the CRUD actions, I made the delete route where the instance of server will be destroyed right after the verification if he is the one logged in.
 
In order to render nice and standerized page I made my style sheets using css in a “main.css” file and in the “layout.erb” file.
 
It is necessary to highlight the fact that during the manufacture of these routes and view pages, I had to make help methods, prived methods and class methods. I also used embedded ruby “<%=   %>” to be able to render and manipulate the data, beside html and css.

 
This project, being the last of many Sinatra apps it was exiting and endearing to make….




