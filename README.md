Node API 1 Project Starter Code
Introduction
Building a RESTful API.
Performing CRUD operations.
Writing API endpoints.
Instructions
Task 1: Project Setup
There are two possible ways to submit your project. Your instructor should have communicated which method to use for this project during the Guided Project and in your cohort's Slack channel. If you are still unsure, reach out to Lambda Staff.

Option A - Codegrade
 Fork and clone the repository.
 Open the assignment in Canvas and click on the "Set up git" option.
 Follow instructions to set up Codegrade's Webhook and Deploy Key.
 Push your first commit: git commit --allow-empty -m "first commit" && git push.
 Check to see that Codegrade has accepted your git submssion.
Option B - Pull Request
 Fork and clone the repository.
 Implement your project in a firstname-lastname branch.
 Create a pull request of firstname-lastname against your main branch.
 Open the assignment in Canvas and submit your pull request.
Task 2: Minimum Viable Product
Use Node.js and Express to build an API that performs CRUD operations on users.

Add a server script to the package.json that runs the API using nodemon.
Write endpoints
Add the code necessary in index.js and api/server.js to create a Web API and implement the following endpoints:

Method	URL	Description
POST	/api/users	Creates a user using the information sent inside the request body.
GET	/api/users	Returns an array users.
GET	/api/users/:id	Returns the user object with the specified id.
DELETE	/api/users/:id	Removes the user with the specified id and returns the deleted user.
PUT	/api/users/:id	Updates the user with the specified id using data from the request body. Returns the modified user
User Schema
Each User resource should conform to the following structure (AKA schema):

{
  id: "a_unique_id", // String, hint: use the installed `shortid` npm package to generate it
  name: "Jane Doe",  // String, required
  bio: "Having fun", // String, required
}
Database Access Functions
You can find them inside api/users/model.js. All of these functions return Promises.

find Resolves to the list of users (or empty array).
findById Takes an id and resolves to the user with that id (or null if the id does not exist).
insert Takes a new user { name, bio } and resolves to the the newly created user { id, name, bio }.
update Takes an id and an existing user { name, bio } and resolves the updated user { id, name, bio} (or null if the id does not exist).
remove Takes an id and resolves to the deleted user { id, name, bio }.
Endpoint Specifications
When the client makes a POST request to /api/users:

If the request body is missing the name or bio property:

respond with HTTP status code 400 (Bad Request).
return the following JSON response: { message: "Please provide name and bio for the user" }.
If the information about the user is valid:

save the new user the the database.
respond with HTTP status code 201 (Created).
return the newly created user document including its id.
If there's an error while saving the user:

respond with HTTP status code 500 (Server Error).
return the following JSON object: { message: "There was an error while saving the user to the database" }.
When the client makes a GET request to /api/users:

If there's an error in retrieving the users from the database:
respond with HTTP status code 500.
return the following JSON object: { message: "The users information could not be retrieved" }.
When the client makes a GET request to /api/users/:id:

If the user with the specified id is not found:

respond with HTTP status code 404 (Not Found).
return the following JSON object: { message: "The user with the specified ID does not exist" }.
If there's an error in retrieving the user from the database:

respond with HTTP status code 500.
return the following JSON object: { message: "The user information could not be retrieved" }.
When the client makes a DELETE request to /api/users/:id:

If the user with the specified id is not found:

respond with HTTP status code 404 (Not Found).
return the following JSON object: { message: "The user with the specified ID does not exist" }.
If there's an error in removing the user from the database:

respond with HTTP status code 500.
return the following JSON object: { message: "The user could not be removed" }.
When the client makes a PUT request to /api/users/:id:

If the user with the specified id is not found:

respond with HTTP status code 404 (Not Found).
return the following JSON object: { message: "The user with the specified ID does not exist" }.
If the request body is missing the name or bio property:

respond with HTTP status code 400 (Bad Request).
return the following JSON response: { message: "Please provide name and bio for the user" }.
If there's an error when updating the user:

respond with HTTP status code 500.
return the following JSON object: { message: "The user information could not be modified" }.
If the user is found and the new information is valid:

update the user document in the database using the new information sent in the request body.
respond with HTTP status code 200 (OK).
return the newly updated user document.
Notes
You are welcome to create additional files but do not move or rename existing files or folders.
Do not alter your package.json file except to install additional libraries or add additional scripts.
In your solution, it is essential that you follow best practices and produce clean and professional results.
Schedule time to review, refine, and assess your work.
Perform basic professional polishing including spell-checking and grammar-checking on your work.
Task 3: Stretch Problems
Be careful not to break MVP while working on these Stretch goals! If in doubt create a new branch.

You'll need to enable the cors middleware:

add the cors npm module: npm i cors.
add server.use(cors()) after server.use(express.json()).
Create a new React application and connect it to your server:

the React application can be anywhere, but, for this project create it inside the folder for the solution.
connect to the /api/users endpoint in the API and show the list of users.
add a delete button to each displayed user that will remove it from the server.
add forms to add and update data.
Style the list of users however you see fit.
