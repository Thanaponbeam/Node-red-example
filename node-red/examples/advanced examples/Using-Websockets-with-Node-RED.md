# Using Websockets with Node-RED
 Websockets are another useful communication capability that is built into Node-RED via the the websocket node. Websockets provide a duplex TCP connection and were designed to allow web browsers and servers to maintain a ‘backchannel’ that could be used to augment traditional HTTP interactions, allowing servers to update web pages without the client making a new pull request.
The websocket node comes in two flavours, input and output, allowing you to listen for incoming data (input) or to send (output) on a websocket. The output version is designed to check to see if the output payload originated at a websocket in a node, in which case it responds to the original sender. Otherwise it will broadcast the payload to all connected websockets.
In addition, both input and output websocket nodes can be configured as either server or client – in server mode they ‘listen on’ a URL, and in client mode they connect to a specified IP address.
To see how the websocket nodes work, you’ll use a public websockets echo server which runs on the public site: ([https://www.websocket.org/echo.html](https://www.google.com/url?q=https://www.websocket.org/echo.html&sa=D&usg=AFQjCNGadI5XRpj4bvWBZ18abDsMoDqLww)).

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-17.jpg)


 Configure the inject node to send a string payload of “Hello There” 

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-18.jpg)


 Configure the websocket nodes to connect to wss://echo.websocket.org 

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-19.jpg)


  Configuring the websocket to send to a public echo server. Do the same for the websocket out node.
 Deploy. When you click on the inject node you will see the message printed out 

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-20.jpg)


