Develop folder Tutorial:

This is a tutorial for the codebase contained in the folder titled Develop. The project contained within it is a Node.js application using Sequelize and Passport. Sequelize is a library in JavaScript that can manage SQL databases.
Passport is an authentication middleware for Node.js

 Files and their purpose:

Server.js:

This is a good place to start as it is often recognized as the main file within a project. At the top of the file variables are established that bring in particular npm packages needed for the project. In this case we require express, express-session as well as passport package as configured.

We then setup a port through environment variables allowing the port to be changed as needed if hosted remotely or using port 8080 locally. The models folder is required for database syncing.

An express app is then created and the middleware required to connect the front end is declared. The public folder is joined to the server and this connection will be necessary for the authentication process. The json and urlencoded components of express allow the application to work with nested JSON. The express app will bring in and require passport for authentication and sessions to manage user login status.

The database is then synchronized providing confirmation to the user if successful.

Package.json:

This is a file that resides in the project root and it contains the npm packages' metadata that is relevant to the project. This file manages dependencies and allows node package manager to recognize the project. The name that npm recognizes for the project can be found at the top of the file after "name". "Main" is the primary file recognized for the application. Packages that are used in the project will be listed under "dependencies".

If no package.json is present initialize setup with npm init -y command in node.js terminal. 

Routes (folder):

The routes folder is used to contain and organize the different dedicated routes for the project. 
	The api-routes file manages the routes used for user authentication. It
first requires the models folder and passport package as we've configured since the route functions are dependent on them. The routes for functions follow the convention where the base url route is followed by /api, followed by a term relative to the function created.The module exports a function that uses the passport authenticate middleware with a local strategy. If the user has the correct login information then they access the members page. If not, the user receives an error. The route for signup uses the sequalize user model to automatically hash and store a users password. If a user is created successfully, then they are directed to the login route. If not, the user is sent an error.The logout route is used to log a user out once logged in. The user_data route is used to retrieve user information so it can be used on the front-end of the application. An if else statement is used so that if the user is not logged in an empty object will be returned. Otherwise the user email and id will be returned.
	The html-routes.js requires path so it can use routes relative routes to
HTML files of the project. The file also requires the middleware created for checking user login status. The root route "/" function will send a user with a recognized account to the members page. The " /login" route function will send a user with a recognized account to the login page. The authentication middleware is then applied to redirect users who are not logged in to the signup page.

Public (folder):

	The public folder contains three html files and two folders. The html files
proved the format and structure that allow the user to provide input and navigate the application. The stylesheets folder contains CSS styling code for the front-end and the js folder contains the client side JavaScript code, which provides functionality.
	The signup.html file includes a navbar and a form with two inputs that
enable a user to input their email and a desired password. The form also includes a button as a signup event. At the bottom of the page, there is a link to the login page to redirect existing users. Members.html provides a navigation bar with a link to the logout page. It also includes a large dynamic header to welcome the user by their name. Login.html includes a navigation bar at the top and a single form for an existing user to provide the email and password associated with their account. At the bottom of the page, there is a link to the signup page to redirect new users.
	The style.css in the stylesheets folder applies a margin-top of 50 pixels to
the signup and login forms on their respective html pages.
	Signup.js file within the js folder first references the signup form as well as
the user email and password inputs. Then, when there is a click event for the signup button we check that the email and password inputs were not empty. If a user and password are present, the signUpUser function is run. This function performs a post to the signup route. If it is successful, then the user is directed to the members page. If not, errors are logged and an alert is thrown. The members.js file performs a GET request to determine what user is logged in then updates the associated html page. Login.js first refences the login form and its email and password inputs. Then, when the form is submitted, it validates if an email and password were provided. If an email and password are present, the loginUser function is run and the form inputs are cleared. The loginUser function performs a post to the "api/login" route and if it is successful, the user is redirected to the members page. If there is an error, an error is logged.

models (folder):

The models folder includes two files index.js and user.js. The user.js file brings in and requires bcrypt for password hashing. A User model is then defined and created. The user email and password must be a string and cannot be null. Then a User model method  is created to verify a password provided by a user against the hashed password that is stored in the database. Hooks automatically run their methods to hash a new password before a user is created. Then the User is returned. The models/Index.js file requires existing utilities like fileshare, uses the path.basename() method to return the filename part of a file path to use with functions, and uses environment variables to manage database connection.  It requires the relative path to config.json in the config folder for sequalize data management. Then a db object is created and exported at the end of the file.
 

path.basename() method returns the filename part of a file path.

Dependent files:

Api-routes.js is requires the models folder. a button to sign-up or This page also provides the user with a link to login if they are an existing user.
	
The signup.html file requires js/signup.js in the public folder for functionality. This file also uses style.css for applying styling to its form.
	
he members.html file requires js/members.js in the public folder for functionality.
	
The login.html file requires js/login.js in the public folder for functionality. This file also uses style.css for applying styling to its form.
	
Index.js in models requires the relative path to config.json in the config folder.