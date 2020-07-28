## Topics covered:
- router stuff 

## General Notes:
- we specify the route and tell the route what path it should handle 
- react router, if both things match, will load more than one component
    - so, you need a switch
    - which says, find the first route that matches 
    - use exact so that the browser doesn't read the first slash over and over again 
- to load the same component on all your pages, put it in the router but outside the switch tags 
- match, location, history
    - history is a way for us to change whats in the url 
    - location is whats currently in the url bar 
- hooks have to start with the word "use"
    - always has to be at the top level, unnested
    - you can only call them from functional components
- <> </> this is called a fragment

## Lab related:
- arrayOf() is used when you're expecting an array
    - .shape allows you to return the shape of the object

## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: