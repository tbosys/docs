#Authentication

Authentication is based on jwt web tokens, baked by 3 tables in the DB: owner, profile, profileOwner.

## Process

For every request we validate the JWT Token and compare it with the existing user in db. We also take the opportunity to load into context the assigned
profiles to that user. Each profile has roles assigned to it, so in the end the user in context ends up with a collection of roles.

Down the line apiHelper/permission is used by action classes ( check /docs/ApiServer.md for more info ) and examine the path of the API request to check if the logged in user has permissions to perform the current actions. The code for this validation is available in /middleware/auth.js

## Login

When a user attempts to login with their email we check if the email is registered to a active owner. If it is, then we create a login passcode and sent it to the registered login. The user then uses the code to securely login into the system. At this point a JWT token is issued and sent to the client to be use in subsequent Api calls.
