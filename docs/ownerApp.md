# How to build the Owner App

This article explains how the Owner App was created.

# Overview

We choose to document the creation of the owner app because of it's complexity. The Owner app is responsible for managing the users, but also the permissions on the users.

User permissions work by adding one or more profiles to a user. A Profile contains one or more roles, and a role is a specific access to a database table, for example create,read,edit access to a table. We assign profiles to users in a many to many relationship called profileOwner.

The Owner application needs to make it as simple as possible to visualize and modify which profiles apply to the specific user. To do this, we need data from the owner ( which we get in the normal way ), the list of available profiles and the profiles that apply to the specific user

In order to do this we create a Standard List App with a custom component to handle permission management in a custom component.

# Architecture

When building apps involving many to many relationships there is always the question of when to save the change to the many to many relationship. In a way, permission management is a secondary action that we decided to accommodate on the Owner Edit Form.

This opens up the question of when this secondary actions save action should occur, at the moment it's done or when the parent owner object is saved. There's patterns for both. We choose the latter.

In api terms, we are sending the modified object as an unrelated field using the "\_" suffix. This way the parent owner object is updated and we use the unrelated fields to create/update/delete the respective profileOwner relationships. There are many patterns to achive this, however we feel that this one is easy to understand, maintain and develop.

# Create the App

- Copy & paste /containers/standardContainerApp into a new folder.
- Edit the container/index.js file in order to add the container App to the menu and the list of apps

# Create the Schema

- Create a regular schema
- Add a component field, by setting the field render property to "component"
- Create a new section with widths: [12,12,12] for the custom component column

# Add Component to App

- Edit the app and import the custom component, then add it to the schema components array property

# Create Component

Create the custom component, custom components must be able to receive it's current value from `props.value` and should update changed with the `props.onChange` function.

# Create API Actions

On the Api in the `/actions/owner` folder create files `create.js` and `update.js`. Then add the required logic which is to use the postCreate and postUpdate functions of the api operations to create or update the profileOwner database table.
