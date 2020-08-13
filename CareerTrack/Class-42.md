## Topics covered:

- Authorization


## General Notes:
- < PrivateRoute path = () component={}>
    - this route will only work if there is a user logged in 
## Lab related:
- auth provider
- useEffect
    - verify

#### Backend
- lib / model
    - user model 
    - add unique: true to email
    - will need a profileimage, no need to make it required
    - npm i bcryptjs, then import into user
    - inside model, write toJSON object to delete ret.__v, and ret.__passwordHash
    - virtual for passwordhash
        - SALT_ROUNDS 
        - the + sign converts the string to numbers
- .env
    - mongo uri
    - salt rounds
- app test js becomes auth test js 
    - first test, signs up user with email password and profile image 
    - .post to auth/signup
    - .then returns response, don't include password here 
- routes/auth.js
    - Router
    - don't forget to change RESOURCE in app.js pathing to /auth
    - .post /signup
    - first npm i cors, then app.use(require(cors)({
        origin:true, 
        credentials: true
    }))
    - origin and credentials are for cookies 
- open up compass / postman
    - in postman:
        - enter url localhost
        - in body, add email and password in one object, we should get back user info 
    - if we got to compass, we should see our user in the database 
    - alternatively, curl
        - curl -XPOST -H 'Content-type: application.json' 'http/:url/signup' -d '{ "email": "email" "password": "password" }'
        - | jq
            - returns pretty result in the terminal 

#### Frontend
- src/ services / auth.js
    - fetch is going to grab .env value via template literal
    - credentials true tells fetch to send cookies 
- .env
    - API URL will start as localhost, but once deployed to heroku, this url will change 
- *eslint
    - globals: {
        process: true
    }
- hooks / AuthContext.js
    - useCurrentUser that will grab the current user
    - useSignup that will grab sign up
    - these values will be grabbed from our provider 
- providers / AuthProvider.jsx
    - bring in children
    - wrap children in AuthContext (which you need to import)
    - provider tags need value={}
    - useState first
    - then signup function
    - now you can pass the signup function to the value bracket in provider tags
- components/auth/Signup.jsx
    - will grab sign up function by using the useSignup hook, which will give us the sign up from auth provider
    - we will need state here as well, Ryan initially made a temporary one 
        - email needs state
        - password needs state
        - profile image needs state 
    - handleChange function 
        - conditionals for email, password, and profile image 
    - return form 
        - inputs for email, passwotd, and url imput for profile image 
        - add name= to each input
        - button
        - onSubmit inside form tag
    - make handleSubmit function 
        - invoke signup function and pass it email, password, and profileimage
- app.js
    - import signup
    - npm start to see if it works 
    - debug:
        - in services credentials: true becomes credentials: 'include'
    - add switch, router, and all that good stuff
- component / header  / header.jsx
    - this component will either render a signup form or the users profile image
    - we already have a useCurrentUser hook which creates a user when they sign up
    - so we need to grab that current user
        - first, conditional ternary using Link
        - then put Header into app.js
        - because no cookies yet, browser resets on page reload 

#### back to Backend
- auth.test.js
    - it logs in a user with email and password 
        - uses async / await 
        - first we need to create a user 
        - .send sends a login request 
        - add profile image for visual diff
- auth.js aka routes
    - .post /login
    - ps. all this below is pseudocode:
    --
    - find a user by req.body.email
    - if that user doesnt exist, error
    - check req.body.passwod matches user.passwordHash
    - res.send(user)
    --
    - write the above code in the model User.js
- User.js
    - authorize schema
    - async / await function taking params of email and password
    - this.findOne looks for email
    - conditional if statements to generate error if user cannot be found
    - passwordMatch conditional statement
        - exclamation point in front of anything always returns boolean
    - back in auth.js, we can now use authorize schema
- auth.js
    - .post /login
    - authorize
    - .then
    - .catch

#### back to Frontend
- auth.js in services
    - const fetchLogin
    - this is the bridge between backend and frontend 
    - you'll notice some duplication code here, to solve this:
        - request.js file
        - make some helpers here 
        - headers need to be conditonal because content-type: application json does not work for GET or DELETE
        - so, create NONBODY_METHODS and conditional ternaries in headers and body accordingly 
        - this is effectively a generic request 
        - now use the generic request in different consts representing methods (post, get, put, patch, del) 
            - del is delete but you can't call it that because the word "delete" is reserved
        - SO NOW, you can use these consts representing methods in auth.js (where fetchSignup and fetchLogin, and other feth calls live) 
- AuthProvider.js
    - const login calling fetchLogin
    - add logint to value in provider tag
- AuthContext.js
    - useLogin
- component /auth / Login.jsx
    - will need useLogin hook
    - temporary state (empty strings)
    - handleChange function
    - form
        - input for email
        - input for password
        - button
    - handleSubmit function, then pass it to the form tag 
- App.js
    - add login route 
    - and let's make sure we can log in back on the browser 
    - login is not yet persistent because we dont have verification and cookies 
- Header.js
    - we could add login link to header
    - to avoid horrendousness, creates AuthLinks component 

## HANDLE ERRORS
- the network tab gives us good error messages, it would be nice to surface (expose!) this error message, to do that, go back your frontend
- request.js in services
    - within the fetch block:
        - .then Promise.all
        - .then ok json
            - conditional statement
- AuthProvider.js
    - signup ang login will now throw errors when erroring
    - useState for authError
    - then add .catch to sign up and login
    - notice duplicate code, which we will fix in a sec 
    - imagination time: setAuthError(null) so that old error messages dont stay displaying 
    - refactor to clean up duplicates:
        - const authService
        - then adjust signup and login 
        - add to value in provider tag
- AuthContext
    - useAuthError
    - because it would be cool to display error messages:
    - component / auth / auth error
- component / auth / autherror.jsx
    - this component will constantly look for error msf and display it in red 
    - this is a convenient component to have because now we can go back to login.jsx and drop AuthError component to the top of our form 
    - debug:
        - autherror.message (AuthError.jsx)
    - we can put this error displaying component wherever you want 

## VERIFY (cookies)
- the request from login now needs to include cookie 
- we will be using json web tokens, jwts
- the backend creates and sets the cookie
- npm i jsonwebtoken cookie-parser

#### back to Backend
- User.js
    - SIGN UP schema.methods.authToken which will create a jwt token for this user
    - bring in jwt in imports at the top
    - we need to provide a secret which we need to put into the .env file
        - in .env, add APP_SECRET
    - expiresIn points to when the token should expire 
    - payload: this.toJSON
        - this refers to an instance of the user login 
    - return token 
    - this set up rn is one directional, we want it to be two-directional, so:
    - LOG IN schema.statics.tokenToUser (use when parsing cookies)
        - jwt.verify
        - sub = subject
        - let's try catch here so that we can make our own error message 
- auth.test.js
    - it verifies a signed up user
    - const agent = request.agent(app)
        - the agent stores the cookies for us 
    - now we need to write the route 
- auth.js (routes)
    - .get(/verify)
    - we need to write a piece of middleware that will verify cookies for us
- ensure-auth.js in middleware
    - store cookies.session in token const
    - const user is what is returned to us when the token is inputted and exists 
    - if it doesnt exist, we need some logic for that -- try catch
    - now back to auth.js to add res.send(req.user)
    - debug:
        - app.use(require) cookie parser in app.js 
- auth.js
    - res.cookie('session')
    - the value of our cookie is user.authToken
        - httpOnly means javascript wont be able to read our cookie
        - max age correlates to the expiresIn 
            - magic number: 1000 * 60 * 60 * 24
            - most people would want you to give magic number a variable: ONE_DAY_IN_Ms
    - const sendUser is a function that avoids duplication of code, since every method attached to auth will need cookie
    - add ", res" to .thens in /signup and /login 
- auth.test.js
    - import dotenv because APP_SECRET
- back in browser -- application (devtools), we should have a session key

#### back in the Frontend
- auth.js
    - const fetchVerify service which will either return logged in user or error message if noy logged in
- AuthProvider.jsx
    - check in if youre logged in with useEffect -- fetchVerify
    - now go back to browser and refresh, your should still be logged in 

## PRIVATE ROUTE
- in front end, dashboard /  Dashboard.jsx
    - only logged in users should be able to see this (hence < Private Route >)
- create special component called Private Route 
    - we need to add more state to our application 
- authprovider.jsx
    - authLoading, seAuthLoading
    - .finally in useEffect
    - add authLoading to value in provider tag
- authcontext.js
    - create and use const useAuthLoading hook
- auth / PrivateRoute.jsx
    - functional component 
    - proptypes
    - route from react router dom 
    - we are going to grab the current user and also loading state 
    - if(!loading && !currentUser) means if theres no loading and no user, then < Redirect > which is baked in I believe
    - props is passed so that private route can work with route 
- app.js
    - PrivateRoute that dashboard component 
- back in Login and Signup components
    - const history = useHistory() (dont forget to import from react router dom)
    - .then in handleSubmit that history.push(es) to /dashboard component


## Question, Go-Back-To:
- dropped off at 2:09 in lecture 
## Progress, Realizations, AHA Moments: