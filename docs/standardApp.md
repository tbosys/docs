# Creating a Standard List App

This is the fastest way of creating an App with table, filtering, create and update

## Process

On the file /containers/index.js add a property to the apps hash. The Property name will be the key to that app and the value should be an array of properties. If the property is a standard one like "id" or "name" of "date" ( check /docs/schema.md for more info ) then simple use a string with it's name, otherwise create a column property with [title,render,filter,default] properties.

## Api

On the Api create a JSON Schema file for the desired object used in the app. A standard app must represent a single db object. There are several other patterns and architectures for more complex cases.

## Menu

You may reference this app on the menu, in the file /container/index.js add the key of he app any section of the menu tree.

You may also not want to add the object to the menu and navigate to it instead from inside any app, such as a standalone action on the actions array on the table section of the app, this requires a bit more frontend code but is just as simple. Check the /container/admin/owner app for a sample architecture.
