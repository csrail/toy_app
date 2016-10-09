##Exploration

Hartl Chapter 2: toy_app

##Eggs

* Q: Create a new user, then use your browser’s HTML inspector to determine the CSS id for the text “User was successfully created.” 
* A: A flash notice saying "User was successfully created" pops up. It is contained within a div given `id="notice"`.

* Q: What happens when you refresh your browser?
* A: The div with `id="notice"` is still present in the html code but contains no content.

* Q: What happens if you try to create a user with a name but no email address?
* A: The user object is created successfully. There is no validation that the email form is filled.

* Q: What happens if you try create a user with an invalid email address, like “@example.com”?
* A: The use object is created successfully. There is no validation that the email is a true one.

* Q: Does Rails display a message by default when a user is destroyed?
* A: Yes - there is also a flash notice on create, update and destroy.

---

* Q: Write out the analogous steps for visiting the URL /users/1/edit.
* A: The GET `/users/1/edit` request is parsed by the rotuer and the Users controller is called on. The controller evokes the `edit` action and, after conferring with the model (who interacts with the database), assigns the data to an instance variable. This instance variable is then used within the `edit.html.erb` view.

* Q: Find the line in the scaffolding code that retrieves the user from the database in the previous exercise.
* A: 

```ruby
# ./app/controller/users_controller.rb
class UsersController < ApplicationController
  def edit
  end
end
```

```ruby
# ./app/models/user.rb
class User < ApplicationRecord
end
```

* Q: What is the name of the view file for the user edit page? 
* A: `toy_app/app/views/users/edit.html.erb`

---

* Q: Edit the user show page to display the content of the user’s first micropost.
* A:

```html
<!-- ./app/views/users/show.html.erb -->
<p>
    <%= @user.microposts.first.content %>
</p>
```

* Q: Adding validation for the presence of micropost content ensures that microposts can’t be blank. Verify this behaviour.
* A: A div contains `#error_explanation`; labels, input and textarea contain `.field_with_errors`. Note the difference of id and class.

* Q: Validate the presence of name and email attributes in the User model
* A: 

```ruby
# ./app/models/user.rb
class User < ApplicationRecord
  validates :name, presence: true
  validates :email, presence: true
end

```