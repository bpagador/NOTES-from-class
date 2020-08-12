## Topics covered:
- flux design patterns 

## General Notes:
- demo on how to read CSV files here, check it out
- hot tip: codepen.io for css playing!!!
    - box-sizing: border-box controls the ultimate size of the box, because border contains padding which contains content
- css by grouping, google search "css tricks polls"
- bitly.com = a cool url shortner 
    - POPULAR INTERVIEW QUESTION, AN EXERCISE WORTH STUDYING 
- res.direct in express allow you to redirect to a new url 

## Lab related:

## MVC pattern (with functional component)

#### backend
- seed.js 
    - csv() allows us to read each line of the csv file (i think its called movies.csv in this demo) and reformat it to our use 
- movies.test.js
    - make sure to path to the csv file logic in seed.js here, in one of the beforeEach
    - bring in csv package up top
    - it search for a movie name by search term
        - uses just a couple (5) objects containing the search term we will be filtering our movies by
- movies.js
    - RegExp
        - we are getting the value of the req.query.search, this query is trying to match the route with "search=Wait" on movies.test.js
        - the "i" makes it case insensitive
        - this ^^^ then changes to .find, $or, which allows us to search by multiple terms  (name, genre, studio)
        - .limit(5) allows us to receive back only 5 responses to our query 
- app.js
    - dont forget cors 
    - change RESOURCE accordingly 
- once test is passing, npm run start:watch and check postman 

#### frontend

- first thing let's make a bridge, so:
- services / movies.js 
    - searchMovies is going to take a search term and its going to fetch via a url with "search" template literal 
    - to get rid of the red squiggly on process, dont forget globals
- .env
    - update with your localhost addy
- lets start with components/ search / searchInput.jsx file 
    - this is a presentational component
    - needs proptypes 
    - value={} and onChange={}
- resultItem.jsx
    - needs proptypes as well 
    - also a presentational component
- searchResults.jsx also in search folder
    - presentational / proptypes
    - this will be returning a list 
    - .map off results and utilize ResultItem
- typeahead search.jsx 
    - it will need to take in a search term
    - it will need to be able to change as the term changes, proptypes.func
    - and a list of results, which will use proptypes.ArrayOf
    - SearchInput and SearchResults components are called here 
- src / containers / MovieSearch.jsx
    - this container will be handling all our business logic 
    - we have to choose between class and functional, what will the component be?
    - this is where all your state will be living 
        - searchTerm
        - movies
    - TypeAhead component gets utilized here
    - in order to be able to type into the box, we will need a handleChange function
    - Typeahead tag will need params: searchterm, results{movies}, onchange 
    - useEffect
        - we want it to trigger when searchterm changes
        - conditional statement so that if there are no searchterms, we have an empty list of movies (setMovies[])
        - we can call our service from movies.js here in useEffect
            - at this stage of the build out, we only want text because our typeahead component is only expecting an array of strings 
            - we have no way of handling objects at this time 
- css on the front end
    - global condition for css can be changed directly in index.js, which will need index.css



## Question, Go-Back-To:
- study MovieSearchClass

## Progress, Realizations, AHA Moments:
- MVC = model (fetch call, service), view (presentational components), controller (containers where state lives)
    - most useful when nest-dolling functionality
        - from api/backend to your own frontend search bar that filters and grabs from api, for example 
        - this works best when you know the exact problem domain and don't expect sharing state with other container siblings 
- I learn best when I take a lot of notes (however, catch 22, i may be more apt at learning through notes because I have fundamental knowledge about what's being shared in lecture and feel like I can balance my attention span over lecture AND notes, where perhaps that wasnt the case when I first started coding)