# Structure of the project
* Website Folder - This folder will contain all of our code for the website
    * static Folder - Assets like images, javascript files, css or anything that is static (which does not change) is stored here.
        * index.js
    * templates Folder - contains all the html templates
        * base.html - Base template
        * login.html - Login template
        * sign_up.html - Signup template
        * logout.html - Logout template
    * `__init__.py` file - This file here, in the _website_ folder is going to make this folder a package. So now, _website_ is a package that we will import and make use of it in the main file.
    * auth.py - Authentication files, like the signup page and login page.
    * models.py - This file will contain our database models.
    * views.py - This file will store all of our main _views_ or the URL endpoints for the frontend aspect of our website.
* main.py - The main file which will are going to run when we want to start our webserver or the website.


## Packages required
* flask
    ```
    pip install flask
    ```
* flask-login - Used for logging users in
    ```
    pip install flask-login
    ```
* flask-sqlalchemy - Used for creating database models
    ```
    pip install flask-sqlalchemy
    ```
