## Topics covered:
* workflow
* what systems will we be working with 

## General Notes:
* primitives: 
    * basic data types
    * new ones introduced here are BIGINT, SYMBOL, NULL, UNDEFINED
* comparison: 
    * === compares types
    * == does not
* logic operators: 
    * && (double ampersand, only returns true when both sides are true)
    * | (or, one side has to be true or the other side has to be true)
    * short-circuiting:
        * for example, when using &&, if the right side is truthy, the left side gets returned
        * therefore, if the right hand side is false, we never get to the left side
        * WITH OR (|) however, we enter the realm of defaulting:
            * if the right side is truthy, the right side returns to us, without evaluating the left side
            * if the right side is falsy, the left side is returned to us
        * ?? - nullish coaslescing
            
## Lab related:
* npm init @alchemycodelab/app
    * node - backend
    * react
    * basic

## Question, Go-Back-To:
* .split
* .reverse
* .join
* .map

## Progress, Realizations, AHA Moments:
