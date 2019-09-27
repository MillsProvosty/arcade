# Arcade

The purpos of this project was to be an introduction to node.js. The learning goals are as follows:
```
- command to generate our Express app
- use Sequelize to create our database
- use Sequelize to generate and run migrations
- set-up the create, read, update, and delete routes
- interact with the database to create, read, update, and delete resources
- create a seed file
```
Arcade uses a Sequelize "promise based" ORM. The Sequelize docs can be found here:
![sequelize](https://sequelize.org/)

### Installation Steps Taken:

1. Go to ![node.js](https://nodejs.org/en/) and install the "Recommended for Most Users" version of node.
2. In the command line, type: ```npm install express-generator -g```.
This allows us to create the start to an Express App, similar to 'rails create'.
3. In the command line, type: ```express --no-view arcade```. The ```--no-view``` is an option that is used so that there isn’t a views folder within our app.
4. In the command line, cd into the project, then run ```npm install```
5. In preparation for building games routes, instead of users, lines 7 and 17 were removed from app.js file.
6. Install the necessary dependencies for our app so that our app can use sequelize and interact with a postgres database by typing in: ```npm install --save sequelize sequelize-cli pg``` followed by ```npx sequelize init```
7. The config/config.json file has three categories that need to be update: username, database and dialect.   
    - Username is the name of your database, found by typing in ```psql``` the ```\q```.
    - The database needs to match the project name, in this case ```arcade_```environment name.
    - The dialect needs to be changed to "postgres" instead of "mysql"
8. Add a .gitignore file, and include node_modules before "initial commit"
9. Create the database by running ```npx sequelize db:create```
10. Generate the model by running ```npx sequelize model:generate --name Game --attributes title:string,price:integer,releaseYear:integer,active:boolean```
11. Migrate the database by running ```npx sequelize db:migrate```
    - In the event a migration needed to be undone, run ```npx sequelize db:migrate:undo```
12. Generate seeds by running ```npx sequelize seed:generate --name game_seed```
13. Create data for seedfile by checking out the sequelize docs ![Here](https://sequelize.org/)
14. Seed the data by running ```npx sequelize db:seed:all```
15. Create Routes with api/v1/model_name.js, such as ```routes/api/v1/games.js```
  - Put the following routes back into your app.js file: ```var gamesRouter = require('./routes/api/v1/games');``` and ```app.use('/api/v1/games', gamesRouter);```
16. Add the following code to your routes file:
```var express = require("express");
var router = express.Router();
var Game = require('../../../models').Game;
```
17. Localhost can be started using ```npm start```
