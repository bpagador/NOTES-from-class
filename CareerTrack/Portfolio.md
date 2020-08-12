- in order to keep header, footer, and main components persisting throughout the site, they will use Router (but no route so that it displays on every page)

- main container will have two children
    - content child
    - image child
    - uses switch so that content changes when new nav link is clicked
    - if image will change on content change, both image and content urls/paths will be the same 
    - NOTE: no Router above Switch 

- redirect for github/linkedin
    - loading spinner: react-spinner npm
    - settimeout 
    - window location (replaced site)
    - _target=blank which will be in a link tag 

- resume 
    - iframe uses src=path_to_asset
    - react-pdf 
    - to make it downloadable:
        - click resume, immediate download happens: `<a href="path_to_file" download="proposed_file_name">Download</a>`
        - resume is displaying in main section and contains a buttom which allows download:
            - component - button onClick
            - filesaver npm 

- contact page
    - email, schedule call, tweet @ me are all anchor tags
    - mailgun for "write me" section 
    
- css - grid
    - maxsize