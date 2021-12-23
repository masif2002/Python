# Walkthrough 
We are going to build a website with Flask using Python. 

* This website is going to allow users to create an account for themselves, log in and start adding notes.
## Steps to create the website
* Build the directory structure
* Initialise the app in `__init__.py` file and use it in main.py file to run it
* Create blueprints for different routes like the home page, signup page.. and register the blueprints in `__init__.py`
* Create base template and which can be extended in other html documents. Then we render our html docs in **views.py** and **auth.py** which contains our webpages.
* Retrieve data sent in forms and validate them.
* Set up our database and create the database models necessary for the project.
* Import the models in `__init__.py` and create the actual database for the project.
* Using the data from the form, start storing users in our database.
* Log in users using flask_login
* Allow users to add and delete notes
---
## Initialization
* Now, we head over to `__init__.py`, to set up our flask application.
* For all our flask application, we have this _config_ variable called "__SECRET_KEY__" which is going to encrypt or secure the cookies and session data related to our website.
    * We can set it to a random string that is going to be the _secret key_ for our app.
    ```python
    from flask import Flask

    def create_app():
        # Initialising a flask application
        app = Flask (__name__)
        app.config['SECRET_KEY'] = "RFIUB#FKJGN"
    ```
* Now, in **main.py**, we are going to import the _website_ package, grab the function we defined to initialise the app, and use it to create an application and run it. When we import a package, the `__init__.py` file is run, and we are allowed to import its entities.
    ```python
    from website import create_app

    app = create_app()

    if __name__ == "__main__":
        app.run(debug=True)        
    ```
    * `debug=True` in `app.run(debug=True)` **automatically** reruns the webserver, whenever we make some changes in our Python code, instead of manually rerunning it everytime we make a change.
* Once we run our main.py file, we are going to see that our website is running and we can access it in the URL displayed in the terminal.
## Creating Routes
* As the webserver is successfully running now, we can go ahead and create our first website _route_. In __views.py__ file, we will be storing our standard routes for our website. Like the home page.. where the users can go to. The login page and the signup page actually goes in the auth.py file since it has to deal with authentication.
    * We now import _BluePrint_ from flask, and tell Python, that this file is going to be the blueprint of our application which simply means, it has a bunch of _routes_ inside it.
    * To actually create views or a route, we use the decorator with the name of the blueprint followed by the path of the route in parantheses
        ```python
        from flask import Blueprint

        views = Blueprint("views", __name__)
        @views.route('/')
        def home():
            return "<h1> Home </h1>"
        ```
    * The function under the decorator will run whenever we go to the specified path (or route) specified in the decorator.
* Now, we have the blueprints for different routes ready and need them to be registered in `__init__.py`
    *  First, we import the blueprints. 
        * When we import entiities from a file in the same folder, we use a `.` infront of the file name. For ex:
            ```python
            from .views import views
            ```
            This imports the blueprint _views_ from _views.py_.
    * Then we register the blueprints in    `__init__.py` using
        ```python
        app.register_blueprint(views, url_prefix='/')
        ```
        * The _url_prefix_ here preifxes the routes inside the blueprint by the specified path.
* Then we do the same in **auth.py** for the login, logout and the signup page and register them.
## Rendering html templates
* Now, we  need to render some html files for each page we have created. In flask, when you render html, you call it a **template**. There is a special templating language that you can use with flask which is called _jinja_. This templating language allows us to write a little bit of Python inside of our html documents.
* Typically, when we make templates, we define a base template. Now, the base template can be seen as the theme of our website. And then we overwite parts of the base template with more specific templates.
* In this tutorial, we use bootstrap classes to syle our website. Bootstrap is a css framework that has some built in classes that makes it alot nicer to style our website.
* According to the _jinja_ templating syntax, we can write pythonic expressions like this
    ```
    {% <pythonic expression> %}
    ```
    * Inside this, we can write a bunch of different things - an if statement, a for loop, or  a block
        ```
        {% if value == True %}
        <h1> True! </h1>
        {% else %}
        <h1> False </h1>
        {% endif %}
        ```
        * We need to end every statement we start. Even if it is an if statement, a for loop or anything. 
* A block is something that can be overwritten when this base template is inherited by any other child template. 
* According to the _jinja_ syntax, we need to end the block we started. For ex:
    ```
    {% block title %}BaseTemplate{ % endblock %}
    ```
* Here, we use bootstrap classes, but if we need to have our own javascript file, we can place it inside the _static_ folder and load them in the base template like this
    ```html
    <script
    type="text/javascript"
    src="{{ url_for('static', filename='index.js') }}"
    ></script>
    ```
    * This is the script we'd write to load in a file called _index.js_ from the _static_ folder.
    * `url_for()` is a python function that loads the url for the _static_ folder in our case. So the attribute _src_ actually stores the url.
    * From above, we also get to know that we can write something like a variable or a function or some pythonic expression inside two curly braces.
        ```
        {{ <pythonic expression> }}
        ```  
* After completing the base template, we define some html documents that can use this base template.
* For the home page, we create a html file called home.html which extends the base template
    ```
    {% extends "base.html" %}
    {% block title %}Home{% endblock %}
    ```
    Here, we extend the base template and the title block from the base template will be overwritten.
* Similarly, for other pages - login, logout & signup we create html pages
* After creating the templates, we need to render them in __views.py__ (for home page) and __auth.py__ (for the rest of the pages because they are related to authentication)
* To render a template, we need to import `render_template` from flask and pass in the name of the html file we like to render.
* _jinja_ templating allows us to pass values to our templates from our backend and displays it in our page.
* To do this, you need to add an extra argument while rendering the template. The argument must be the name of the variable (user-defined) along with its value. For ex:
    ```python
    from flask import Blueprint, render_template

    auth = Blueprint("auth", __name__)
        
    @auth.route('login')
    def login():
        return render_template("login.html", text="Hello")
    ```
    * Here, _text_ is the variable we like to pass in to the template. This variable can be accessed inside the double curly braces in the specific html template. 
    * You can also pass multiple variables seperated by commas.
        ```html
        {% extends "base.html" %}
        {% block title %}Login{% endblock %}
        {% block content %} <h1> This is the login page </h1> 
        {{ text }} <! --- Variable that we passed --->
        {% endblock %}
        ```
* When creating forms for the signup page, or login page or whatever, we should add the attribute, _name_ and set it to a reasonable name. Because this is actually the name that we are going to use for that particular field in the backend.
    ```html
    <div class="form-group">
        <label for="email">Email Address</label>
        <input
            type="email"
            class="form-control"
            id="email"
            name="email"
            placeholder="Enter email"
        />
    </div>
    ```
## HTTP Requests
* Some of the HTTP requests are
    * GET request/method
    * POST request/method
    * PUT request/method
* The URL needs to know what type of request is sent so that they can respond accordingly.
* Typically, a **GET request** is when you're just loading a website, basically retrieving information.
* A **POST request** usually means that you're making some kind of change to a database or something. When we signup or log in, we POST, means we're sending in a POST request with all of the information in our form to our sever. So, our server needs to interpret that and respond to us.
* So, in our pages ie- the login and signup page, we need to make sure that it is able to accept POST requests. 
    * To do that, we need to add another argument inside our decorator.
        ```python
        @auth.route('sign-up', methods=['GET', 'POST'])
        def sign_up():
            return render_template("sign_up.html")
        ```
    * By default, we only accept GET request, but by adding this to a list like this, we are able to accept both, GET and POST requests.
* Now that our forms can accept POST requests, we need to access the data that was sent in the form. 
    * To do this, we need to import _request_ from flask and access the form data
        ```python
        @auth.route('login', methods=['GET', 'POST'])
        def login():
            data = request.form
            print(data)
            return render_template("login.html")
        ```
        * Whenever you access the _request_ variable inside a route, it'll have information about the request that was sent to access this route. 
        * `request.form` prints out an Immutable dictionary object containing the data as key-value pairs.
        * But here, we access the data of the request irrespective of the type of the request, ie- Even if it is a GET request, we print the data, which returns an empty dictionary. So we add an if statement to check the type of request and act accordingly.
            ```python
            if request.method == 'POST':
                pass
            ```
## Message Flashing
* Now, that we have access to the data, we need to access all the attributes seperately and add a few conditions to validate the data.
    * To get the specific attribute in the ImmutableDictionary, we can make use of the get() method.
* If the data is not valid, we can do something called **message flashing**, where it displays some message to the user.
* To do this, we need to import _flash_ from flask and use this method whenever we need to flash a message. We pass in the message to this method, and also add a parameter called _category_.
    * The value for the _category_ parameter is our choice. Based on that value, ie - for different type of categories, we will be styling our display messages accordingly, in our html templates.
    ```python
    @auth.route('sign-up', methods=['GET', 'POST'])
    def sign_up():
        if request.method == 'POST':
            email = request.form.get('email')
            firstName = request.form.get('firstName')
            password1 = request.form.get('password1')
            password2 = request.form.get('password2')
            user = User.query.filter_by(email=email).first()

            if user:
             00+   flash('Email already exists!', category='error')
            if len(email) < 6:
                flash("Email too short!", category='error')
            elif (firstName < 3):
                flash("Name must be a minimum of 3 characters.", category='error')
            elif (password1 != password2):
                flash("Passwords don't match!", category='error')
            else:
                flash("Account created successfully!", category='success')
                
        return render_template("sign_up.html")
    ```
    
* We've implemented message flashing in the backend, but we haven't done anything in the html pages to view the message. So we need to go to our sign_up.html or the base template and do the necessary.
    ```html
    {% with messages = get_flashed_messages(with_categories=true) %}
    {% if messages %} 
        {% for category, message in messages %} 
            {% if category =='error' %}
        <div class="alert alert-danger alter-dismissable fade show" role="alert">
        {{ message }}
        <button type="button" class="close" data-dismiss="alert">
            <span aria-hidden="true">&times;</span>
        </button>
        </div>
            {% else %}
            <div class="alert alert-success alter-dismissable fade show" role="alert">
            {{ message }}
            <button type="button" class="close" data-dismiss="alert">
                <span aria-hidden="true">&times;</span>
            </button>
            </div>
            {% endif %}
        {% endfor %} 
    {% endif %} 
    {% endwith %}
    ```
## Setting up our database
* Now that, we have all the data extracted neat and clean, we need to store this data in a database. So, we head over to our `__init__.py` file and set up the database.  
    * First, we need to import SQLAlchemy from flask_sqlalchemy.
        ```python
        from flask_sqlalchemy import SQLAlchemy

        db = SQLAlchemy()
        DB_NAME = "database.db"
        ```
        * *db* is the database object and *DB_NAME* is the name of our database.
* Once the database is created, we need to tell flask, we are going to use this database, and where the databse is going to be located.
    ```python
    app.config['SQLALCHEMY_DATABASE_URI'] = f"sqlite:///{DB_NAME}"
    ```
* Then, we initialize the database passing in our flask app
    ```python
    db.init_app(app)
    ```
* If we want to store something in our database, we need to define the schema or a layout of what the object is going to look like. So now, we need to define some database models in _models.py_. We are going to create two models here, one for Users and another one for Notes, which the User is going to create, in their accounts.
    * A **database model** is just like a layout or a blueprint for an object that is going to be stored in our database. 
    * First, we import our database object into _models.py_, create a class for our actual model, and inherit from db.Model.
        ```python
        from . import db
        from flask_login import UserMixin

        class User(db.Model, UserMixin):
            id = db.Column(db.Integer, primary_key=True)
            email = db.Column(db.String(150), unique=True)
            first_name = db.Column(db.String(150))
            password = db.Column(db.String(150))
        ```
        * We also inherit from UserMixin so that later we can use an object called *current_user* from *flask_login*, to access the information about the currently logged in user.
        * And inside the class, we define all the coulmns in which we want to store our data.
        * For all of our objects (users in this case), we need to have a primary key. **Primary key** is a unique identifier, with which we can access our object. In our model, _id_ is our primary key, which is the unique identifier.
        * By default, when you add a new object, you do not need to define it's _id_. It'll be automatically set for you. (So that they are unique)
        * When creating a column of datatype String, we need to specify the max length of the string in parantheses.
        * `unique=True` means, the specific field needs to be unique. In our case, we cannot have emails that are identical.
* With that, we've set up our User model. So we're going to store all our users in that layout. Next, we need to set up our Note model.
    ```python
    from . import db
    from flask_login import UserMixin
    from sqlalchemy.sql import func

    class Note(db.Model):
        id = db.Column(db.Integer, primary_key=True)
        text = db.Column(db.String(10000))
        date = db.Column(db.DateTime(timezone=True), default=func.now())
        user_id = db.Column(db.Integer, db.ForeignKey('user.id'))
    ```
    * All of our notes must belong to our user. To associate the note, with the user, we need to set up a relationship between the note object and our user object. We do this in the form of a foreign key.
        * A **foreign key** is essentially a column in your database that always references an column of another database.  
    * So in this case, for every single _note_, we want to store the _id_ of the user, who created the note. So here, the *user_id* column, is always going to store the _id_ of one of the user. 
* Now, with each note, we can reference who created it. But we also want from the user's side to find all of their notes. So we set up a _notes_ field on our _User_ model.
    ```python
    notes = db.relationship('Note')
    ```
    * This line pretty much tells flask, that everytime we create a note, add it into the user's _note_ relationship.
    * Now, we'll be able to access all of the notes the user has created, from this _notes_ field.
## Database Creation
* Now, that we've finished setting up the database, we need to actually create the database in `__init__.py`. But first, we need to import it, so that our models.py file runs and loads all the classes we've created in it.
    ```python
    from .models import User, Note
    create_database(app)
    ```
    create_database()
    ```python    
    def create_database(app):
        if not os.path.exists('website/'+ DB_NAME):
            db.create_all(app=app)
            print("CREATED DATABASE!")
    ```
    * Here, we check if the database is created, by checking if the database file exists in our project folder. If it is not, we create our database.
* Once the database has been created, we can start storing our data from the sign-up form in our database.
    * But, while storing passwords, we cannot directly store it as plaintext but we need to _hash_ it. **Hashing** is essentially a way to secure your password.
        * Hashing function is a one way function. It cannot be inverted. A hash can be generated using a password, but with the hash, we can never get the password. 
        * Typically when trying to log in, we run the password in a hashing function, and if that hash matches the hash stored in the database, that means the password is correct. 
        * To do this, we need to import the function from flask_login.
        ```python
        new_user = User(email=email, first_name=first_name, password=generate_password_hash(password1, method='sha256'))
        ```
        * The parameters inside the User object are just the fields created in our User model.
        * 'sha256' is just a hashing algorithm.
    * Once we've created the database object, we need to add it to the database and then commit it, just like we do in GitHub :)
        ```python
        db.session.add(new_user)
        db.session.commit()
        ```
* After the data is stored, we redirect the user to our home page with the help of the _redirect_ function we import from flask.
    ```python
    return redirect(url_for('views.home'))
    ```
    * The `url_for()` function (which also needs to be imported from flask) just gets the URL to the specified page. ie- The home page in this case, whose route is defined in _views.py_. We are basically finding the URL which maps to the home() function in _views.py_. 
* Now that we are done with the sign-up page, we can go ahead and validate the login credentials.
    ```python
    @auth.route('login', methods=['GET', 'POST'])
    def login():
        if request.method == 'POST':
            email = request.form.get('email')
            password = request.form.get('password')
            
            user = User.query.filter_by(email=email).first()

            if user:
                if check_password_hash(user.password, password):
                    flash('Successfully Logged in!', category='success')
                    return redirect(url_for('views.home'))
                else:
                    flash('Incorrect Password!', category='error')
            else:
                flash('Email does not exist!')

        return render_template("login.html")
    ```
    * `User.query.filter_by(email=email).first()` returns the first user, with the specified email in the database _User_. Technically, we are going to have only one user with that email since the email field is set to be unique in our database.
        * Here, in the login page, we check if the user exists, and then go ahead. We also need to do the same in sign-up page. If a user already exists with the given email, we need to prompt the user to enter a different email.
    * The `check_password_hash()` function checks if the password hash in the User databse is equal to the password received in the login form by hashing it.
        * Note that, the first argument must be the actual hash, and the second argument must be the password that needs to be hashed and checked. 
## Using flask_login
* We saw, how we logged in after validating the credentials from the database. But, we didn't actually login, but just flashed a message saying that we've logged in successfully.
* So now, we import *login_user*, *login_required*, *current_user* and *logout_user* functions from *flask_login*.
    ```python
    login_user(user, remember=True)
    ```
    * This just logins the user. We need to pass in the user object.
    * `remember=True` remembers the user, even after the session expires.
* Now, we define the logout function in _auth.py_.
    ```python
    @auth.route('/logout')
    @login_required
    def logout():
        logout_user()
        return redirect(url_for('auth.login'))
    ```
    * `logout_user()` logs out the current user. We don't need to pass in the user object.
    * We'll also add a decorator, which makes sure, that we cannot access the logout page, unless the user has logged in.
    * After logging out, we redirect to the login page.
* We also add the *login_required* decorator to the home page in _views.py_ because we don't want to access the home page unless we're logged in.
* Now, the last thing we need to do here, when using *flask_login* is we need to tell flask, how we actually log in a user.    
    * To do this, we go to the `__init__.py` file, and import LoginManager from flask_login. 
        ```python
        login_manager = LoginManager()
        login_manager.login_view = 'auth.login'
        login_manager.init_app(app)

        @login_manager.user_loader
        def load_user(id):
            return User.query.get(int(id))
        ```
        * We need to specify where we need to go if we are not logged in. `login_view` helps us to define that. 
        * `load_user()` function is just used to  tell flask, how we load a user. 
        `User.query.get()` works similar to *filter_by()* except by default it looks for the *primary key*.
* We've defined everything, but we need to show it in the page, which means we need to modify stuff in our html templates. 
    * `current_user` which we imported from flask_login has a lot of attributes, which will help us to validate if the user has logged in or not. So, we pass this this as an argument while rendering the html templates.
        ```python
        @views.route('/')
        @login_required
        def home():
            return render_template("home.html", user=current_user)
        ```
        * It necessarily not needs to be 'user' because it's just another variable that we are trying to reference in our templates. Like we said earlier, we can pass variables to our templates. This is just a variable like that.
        * Similarly, we also do it for the login page and the sign-up page.
    * Now, we add the conditions in base.html, since that is where our icons are defined.
        ```html
        {% if user.is_authenticated%}
          <a class="nav-item nav-link" id="home" href="/">Home</a>
          <a class="nav-item nav-link" id="logout" href="/logout">Logout</a>
          {% else %}
          <a class="nav-item nav-link" id="login" href="/login">Login</a>
          <a class="nav-item nav-link" id="signUp" href="/sign-up">Sign Up</a>
          {% endif %}
        ```
## Adding Notes
Now that we're almost done, we need to complete the main objective of the website, we need to allow our users to add notes. 
* To do that, we complete our frontend first, by adding a text area, where users can type their notes and add it using a button.
* Then, we go to _views.py_ and make our changes, since home page is the page that is going to hold our notes.
    ```python
    @views.route('/', methods=['GET', 'POST'])
    @login_required
    def home():
        if request.method == 'POST':
            text = request.form.get('note')
            note = Note(text=text, user_id=current_user.id)
            db.session.add(note)
            db.session.commit()
            flash('Note created successfully!', category='success')
        return render_template("home.html", user=current_user)
    ```
## Deleting Notes
Now, to delete the note when we click on the X symbol, we'll have to define a javascript function. This is the standard way to do it, but there are  otherways to do it aswell.
```html
<button type="button" class="close" onClick="deleteNote({{ note.id }})">
```
* We are going to create this javascript function in the file *index.js* which we created at the beginning of our project.
    ```javascript
    function deleteNote(noteId) {
        fetch("/delete-note", {
            method: "POST",
            body: JSON.stringify({ noteId: noteId }),
        }).then((_res) => {
            window.location.href = "/";
        });
    }
    ```
    * `fetch` is used for sending a request in javascript.
    * This function takes the noteId that we pass, and it sends a POST request to the `delete-note` endpoint (nothing but another route), and once it gets a response from the delete-note endpoint, it's going to reload the window [`window.location.href = '/'`].
    * This is how we send a request to the backend from javascript.
    * This function basically just acts as a carrier between the frontend and the backend. On the buttonClick in the html home page, we call the javascript function, which sends a request to the backend with the noteId and then the note is deleted from the database.
* But, we haven't created the `delete-note` route yet. So, we go back to _views.py_ and do it. 
    ```python
    views.route('/delete-note', methods=['POST'])
    def delete_note():
        note = json.loads(request.data)
        noteId = note['noteId']
        note = Note.query.get(noteId)
        if note:
            if note.user_id == current_user.id:
                db.session.delete(note)
                db.session.commit()

        return jsonify({})
    ```
    * Note that, here, we accept only the POST request and we need to import the json library and jsonify from flask.
    * This method takes in the data from a POST request, loads it as a json object or a Python dictionary, and then access the noteId attribute. Then, we look for the note that has the specific noteId and check if it exists. If it exists, we verify the owner of the note, by comparing the user_id and then we delete the note and return an empty response.

With that, we are finally done with building our website with flask :)