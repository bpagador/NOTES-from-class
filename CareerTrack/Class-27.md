## Topics covered:
- react stuff

## General Notes:
- functional components gets passed prop as its first paramater 
- class components gets passed a this.props
- typechecking is used to keep the readability of our app higher 
    - it asks, what type of thing does it want me to pass it?
- functional components: .propTypes defines the expectattion of the parameter
    - MyComponent.propTypes = {title: PropTypes.string.isRequired} ; this tells the story of the prop type should be 
    - import PropTypes from 'prop-types'
- for static components: static.propTypes = ...
- passing props syntax is the same for func and class components
- good ole state
    - can change 
    - each key value pair is a part of state ( a form of state)
    - scope matters!
- independent state change, independent of previous state = this.setState { keyWeWantToChange: newValue}
- dependent state change; depent on previous state = this.setState( prevState => ({ newStateFunc: prevState.newStateFunc +1 }))
- state provider a component that can pass state to another component
    - it does this via props 
    - which means they're read only 
    - for the other component to have changing state, they need to use functional events that exist in the parent component

## Lab related:
- we will build a page 
    - input and submit button at the top
    - input will output the url
    - list of all the links of the url
- we will be using 2 APIS
    - short url api
    - links api 
- in proptypes library, functions are "func"
- npm start to run react app
- css refresher = class name css convention is .theComponent
- lab will be using css modules (part of webpack, which is assigning the class name a random string)
    - modules uses styles.theComponent
    - modules: true in webpack to make this feature work 
- when doing snapshot testing, when shallowly rendering, feel free to use hard coded data as values for the keys 
    - make sure to doublecheck snapshot to ensure it looks how you expect 
- NOTE app.jsx actually displays the frontend, test your building blocks here
- remember PropTypes.arrayOf(PropTypes.string).isRequired 
- services directory
    - files here will make api calls 
    - we are doing this because we want to make layered architecture 
- the parent component will render its children component
## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: