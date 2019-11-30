# Getting Started
> This page is an overview of the TbOS documentation and related resources.

TbOS is production ready, fully operations and key-in-hand.

TbOS offers:
* open-source: MIT License - an honest gift to the world
* cloud-native: Invented in 2019 exclusively for the AWS Cloud
* serverless: No moving parts, no maintenance, no engineers required, enterprise grade resilience.
* medium-code: Coding is required to create and change apps - we don't believe in click&build.
* distributed: Deployed to 3 geographical locations with automatic switching if one fails. Think automatic backup & recovery

## Pre-requirements
Node
1. Install NVM to manage [node](https://nodejs.org/en/) using the following [guide](https://github.com/creationix/nvm#installation)
1. Install node version **v10.15.0** as a minimum using the following [guide](https://github.com/creationix/nvm#usage)

🤖 Packages are managed using NPM, so please ensure you use the `npm` command as opposed to `yarn` or any other node package manager.

MySQL
1. Install MySQL using the following [guide](https://dev.mysql.com/doc/mysql-osx-excerpt/5.7/en/osx-installation-pkg.html) 
1. Create a new data base schema names `dev` 
1. Export the root data base password by adding `export DB_PASSWORD=xxxxx` to your .bash_profile or by running it in your console
- - -

## Installation

#### API
1. First clone or download the [API repo](https://github.com/tbosys/api) from github
2. In your command line, navigate to the API folder. Eg: `cd ./api`
3. Install the project dependencies using `npm install`
4. Run a migration to your local data base running `knex migrate:latest`
5. Execute the knex seed by running `NODE_ENV=development knex seed:run`


#### UI
1. First clone or download the [UI repo](https://github.com/tbosys/admin-ui) from github
2. In your command line, navigate to the API folder. Eg: `cd ./ui`
3. Install the project dependencies by running `npm install`


## Running development

#### API
1. Navigate to the API folder
2. Start the development server by running `npm start`

#### UI
1. Navigate to the UI folder
2. Start the React development server by running `npm start`


