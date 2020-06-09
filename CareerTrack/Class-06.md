## Topics covered:

## General Notes:
* DNS takes normal names and translates them to IP addresses
* once we have the IP address, we can start making our normal http traffic 
* client-side code : code that runs on a client (React for example)
* server-side code : code that runs on a server (Express, for example)
* tcp and net tell us about our connection 
    * 3 part handshake
        * the client sends a message to a server, to ask if the server is even there -- SYN
        * the server responds telling it that it is there --SYN ACK
        * and then the client acknowledges that it got the message -- ACK
        * this is called a duplex server - the phone works both ways pipe of communication
* (req, res) in express(method) routes is an express handler
* with http we say that the person that established the connection is sending a single response to the pipe
    * and then the server sends back another single message through the pipe 
    * and then the connection is terminated 
* does maggie appleton have a graphic for this? or are there graphics in general about this?

## Lab related:

## Question, Go-Back-To:

## Progress, Realizations, AHA Moments: