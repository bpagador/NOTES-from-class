## Topics covered:
- Redux

## General Notes:

- dispatch method:
    - store.dispatch()
    - const store = createStore (reducer, initialState) is the equivalent of redux to const [state, dispatch] = useReducer(reducer, initilState)
- subscribe method:
    store.subscribe() takes a function and invokes that function whenever state changes

- state method:
    - returns the current state (state)
    - store.getState()

- scaffolding a redux application
    - reducers 
        - initialState
        - create function reducer (state, action)
            - switch on action.type
            - start with default, always
            - export store from store.js (replaces context we were doing before)
- npm i react-redux
    - creates a provider for us
    - "you can do it, little npm!"
    - inside index js, add Provider given to us by react redux, wrap App in it
        - don't forget Provider store={store}
    - import Provider from redux 
- scaffolding a redux application (continued)
    - actions
        - start test (characterActions)
        - open action file (characterAction.js) side by side 
        - in action file
            - create setState (setCharacters) function
    - go back to characterReducer, and make a characterReducer test
        - bring in the SET_CHARACTER constant
- selector help you grab state
- reducers helps manage transitions of that state
- actions help manage how you want to change the state 
- tests are taking place of the components 
- functional components do not need props here
- whenever we are changing state we need to use the useEffect hook!
    - in this demo, to fetch a list of characters we are going to need a service 
    - in useEffect, use the service created
    - to dispatch state change, we need const dispatch = useDispatch() and .then implement it off characters 
- redux tools chrome extension set up
    - go to redux docs, get window line from basic set up 
    - import that line from doc into store.js
## Lab related:

## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: