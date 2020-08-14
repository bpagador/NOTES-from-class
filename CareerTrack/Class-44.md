## Topics covered:
- logout button for terrible movies app
- pagination in movie list from class 43

## General Notes:

#### in the backend (terrible movies)
- in auth.js 
    - create a new route for /logout 
    - here you have to match the syntax of the cookie parser (httpOnly)
#### frontend
- auth.js
    - build a bridge for logout, aka fetchlogout
- authprovider
    - bring fetchlogout here and useCurrent user
    - expose it as a value in the provider tag
- authcontext
    - useLogout 
    - you can use this hook anywhere in your ap
- component/ auth/ logout
    - no need for props
    - onClick, call logout function 
    - now where do you wanna put it? 
- component / auth / header
    - verifiedUserDisplay

#### in the front end (movie list from class 43) 

- PAGINATION:
- in MovieList.jsx 
    - set page state 
    - map through setMovies
    - create pagination buttons 
- in the backend
- movies.js
    - set up blank default_movies_per_page
    - add const {page = 1 ... DEFAULT_MOVIES---} = req.query
    - if we are on page one we want SKIP to 0 item and return the next 5 items in the index, on page 2 we want map to skip the first 5 in index and return the next 5, on 3 we want map to skip 10 in the index and return the next 5
    - add .skip under limit 
    - .then count, getTotalPages from up top
- in the front end
- movieList
    - totalPages from backend can now live in the front end as sate and be added to useEffect 
    - dont forget to disable buttons 
    


## Lab related:


## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: