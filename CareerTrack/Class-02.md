## Topics covered:
- Review Class-01
- 

## General Notes:
* Review from yesterday:
    * .entries gives back both the key and the value as objects in an array, making the objects easier to manipulate 
* id: expect.any(Number) expects any number as an id
    * another hack = id: Date.now()
* console.log is an object and can be equated to jest.fn()
* think of documentation for any system as library that helps you execute a method you've been ideating to solve a problem 
* write the test first!
* switch syntax:
    * ```
    switch( param.method || param1, param2 ) {
        case 'nameOfCase':
            //do this
            return function(param);
        // otherwise, do this if the result is anything that is not defined in the case
        default:
        return;
    }
    ```
* .toBeUndefined : a method saying if this is undefined...
* ternaries are IF ELSE, but you can't use ELSE IF
    * you can use return in ternaries


## Lab related:
* update syntax from class-01 according to code-along from lecture 

## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: