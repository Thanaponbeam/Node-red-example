# Using the switch node to handle a JSON object
 One of the nice features of having a JSON object is that you can easily act on its properties. A useful node for this is the switch node. Its role is to ‘switch’ or route messages depending on the incoming message properties.  For example, you can check the msg.payload.analyze property and, depending on its value (true/false), decide to route a message to one of the switch node’s outputs. Drag a switch node and double-click on it. Configure it to evaluate the property “msg.payload.analyze”. If true, send the message to the first output; if false, send it to the second output.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_BC8B44EF7B842B70DA26FD6184A2C003E8410EA1D972D8389533BEFE3A830EB2_1541957777699_SW1.PNG)


 Now you can connect two debug nodes when you set up multiple outputs for a node, they are numbered from the top, so output 1 is the top output and output 2.
 You go back to the HiveMQ input page and send the MQTT message {“analyze”:true, “value”:6}, you will see that the first (top) output is activated and the incoming messages is routed, or ‘switched’, to output 1. If you send the original message {“analyze”:false, “value”:10}, the switch node will activate output 2 and the original debug node will fire. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_BC8B44EF7B842B70DA26FD6184A2C003E8410EA1D972D8389533BEFE3A830EB2_1541957921018_sw2.PNG)


 Hovering the pointer over the debug message will show which debug node is printing out the message.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_BC8B44EF7B842B70DA26FD6184A2C003E8410EA1D972D8389533BEFE3A830EB2_1541957837409_sw3.PNG)


