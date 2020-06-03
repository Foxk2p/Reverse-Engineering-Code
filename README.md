# Reverse-Engineering-Code

Develop Folder Tutorial:

This is a tutorial for the codebase contained in the folder titled Develop. The project contained within it is a Node.js application using Sequelize and Passport. Sequelize is a library in JavaScript that can manage SQL databases.
Passport is an authentication middleware for Node.js

Package.json:

This is a file that resides in the project root and it contains the npm packages' metadata that is relevant to the project. This file manages dependencies and allows node package manager to recognize the project. The name that npm recognizes for the project can be found at the top of the file after "name". "Main" is the primary file recognized for the application. Packages that are used in the project will be listed under "dependencies".

If no package.json is present initialize setup with npm init -y command in node.js terminal.

Server.js:

This is a good place to start as it is often recognized as the main file within a project. At the top of the file variables are established that bring in particular npm packages needed for the project. In this case we require express, express-session as well as passport package as configured.

We then setup a port through environment variables allowing the port to be changed as needed if hosted remotely or using port 8080 locally. The models folder is required for database syncing.

An express app is then created and the middleware required to connect the front end for the authentication process is established. The express app uses passport for authentication and sessions to manage user login status.

The database is then synchronized providing confirmation to the user if successful.
