# Server

TbOS is serverless. API requests are handled by API Gateway and the parsed body, headers and querystrings are passes as inputs to one Lambda Function using Proxy Integration. The Lambda function checks the path, performs validations and routes the request.

TbOS used middy middleware system which divides the code of the request into layers of middleware. Authentications, DB Access, Routing, Parsing, Error Handling are all middleware files located in the /middleware. They add data to the context and format the response ( successfull or not ) in a way that's interpreted by Gateway API to be passed to the client. There are many caveats on the integration between API Gateway and Lambda, all handled by the middleware layers.

For people interested in modifiying the operation of the "server-less" function understand of middy is essential. After reading middy docs review the few lines of code of /handler.js where the middleware are organized.

## Schema

Normally, each route corresponds to a DB Table. However this is not necessary. The typical approach involves creating a JSON schema file that represents each column on the table and other details of the route such as one-one or one-to-many relationships.

## Automatic Routes

With a JSON Schema in place; query, read, create,update and delete routes are generated dynamically. The automatic classes are located at /operation/baseQuery /operation/baseCreateAction /operation/baseUpdateAction /operation/baseDeleteAction

### Query

The class /operation/baseQuery contains all the logic to generate queries with automatic joins and advanced filtering. There is a section of the documentations dedicated to this at /docs/filtering

## Route Override

To override and take control of an automatic route simply create a get.js, create.js, update.js or delete.js file con the folder actions inside a subFolder which names matches the route.

All mutation routes are formed of several steps:

- preValidate: Executed before the body of the request is validated against the JSON SCHEMA. Sometimes
- preTransform: Executed before the body is transformed, for example injecting
- preCreate/preUpdate/preDelete: Executed right before the body is sent to the DB
- postCreate/postUpdate/postDelete: Executed right after the body is sent to the DB and contains the results of the operation.

You don't have to override every method, just the ones you need which typically are pre for transformations or post for action composition.

## Manual Routes

You may also create custom routes, which have access to context objects that include knex, errors, currentUser and other helper functions. Check out docs/middleware to understand which helpers are available to manual routes.

To create a manual route create a class file on the /action folder under a subfolder with the name of your manual route. You should extend the class operation/baseAction and create at least the execute method.

## Composition

At some point you may need to create or update another DB object. You may perfectly use the knex context object and do it directly. But then you'll miss any business logic specific for that object, such an overriden create route. In this case you may use the helper `createAndInvokeAction` it takes three arguments `(ROUTE_NAME<string>, ACTION_NAME<string>, PAYLOAD<object>,CHECK_PERMISSIONS<boolean>)`. Using this simple helper you may compose complex business requirements, and at the same time follow complex business rules in a very simple manner.

## Security

Automatic routes are checked agains the /apiHelpers/security. The current user must have either global route permissions `TABLENAME_*` or specific permission for the automatic or manual action being performed `TABLENAME_GET` `TABLENAME_CREATE` `TABLENAME_UPDATE` `TABLENAME_DOCUSTOM`

By default route permissions are extended to composed operations. For example if the user has access to an specific route, and that route uses composition of other actions then by default is assumed that the user has permissions to do those actions as well. If you'll like to validate actions down the line, then simply pass true as the last argument to createAndInvokeAction

## Transactions

All actions are automatically enclosed inside a transaction that automatically commits at the end of the promise chain returned by the first action's execute method. If anyone of those promises throws and error, then the transaction is rollback and the error is forwarded to the client.
