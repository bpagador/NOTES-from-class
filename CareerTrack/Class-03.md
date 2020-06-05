## Topics covered:

## General Notes:
* in postgres, you can highlight the bit you want to see in the table
* mongodb scales horizontally
* sql scales vertically 
* db.getCollection
    * .insert
    * .find
    * .findOne
* you can use mongodb without mongoose but not mongoose without mongodb

## Lab related:
* npm i mongoose - to install dependencie
* lib / models
* name the model in upper case ang singular 
* import mongoose 
* create a schema which tells us what the data model should have in it 
    * provide objects inside curlies 
        * each object has a type and required (if it is required)
* export mongoose via module.exports 
* in and index.js, create your data
* use compass (like pgadmin but for mongodb) to monitor/validate the data
* commands you can use re: CRUD:
    * .find()
    * .findByIdAndUpdate
    * .findByIdAndDelete
    * .then
* { new: true } tells compass to return an updated object

* npm i -D mongodb-memory-server allows us to start our server from vscode (enabling the equivalent npm run test:watch for mongodb)
    * import MongoMemoryServer (a library) into your test file
    * open (beforeAll - start mongodb and connect mongodb) and close(afterAll - disconnect mongodb and close mongodb)  
    * beforeEach restarts the server with updated information (I think)

## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: