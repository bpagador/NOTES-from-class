## Topics covered:

## General Notes:
* unit tests test modular functionality 
* integration testing tests how things are connected, for our case that the backend and the front end are working
* acceptance tests, the server might be depent on someone else's tests 
* rest convetions worth noting:
    * PUT updates a whole resources
    * PATCH partially updates a resource 
* express pathing with params
    * res.end(req.params.thing) corresponds to a :thing in the url path

## Lab related:
* init alchemycodelab
* select node
* in server.js, we are connecting to mongodb on line 2
* in lib dir, connect js connects to mongodb
* in services folder, external APIs
* models, mongoose folders
* routes, all of our routes files 
* you will need to create an .env file to hold your secrets
* RESOURCE is a place holder in app.js  
* try/catch syntax for routes
```
    Model
        .find()
        .then()
        .catch(next)
```
* models files are singular and upper case
* routes files are plural and lower case 
* app.js will use the routes
* routes will need to define and export { Router }


## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: