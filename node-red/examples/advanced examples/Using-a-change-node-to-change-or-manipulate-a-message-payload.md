# Using a change node to change or manipulate a message payload
 You can use this node to affect the properties in a message, either by changing existing ones, deleting them or adding new properties. In this example, you’ll continue with your MQTT theme and see how, now that you have successfully ‘switched’ the message flow based on the incoming MQTT message, you can add a new message property msg.payload.note.
Drag and drop a change node and connect it to the second output of the switch node. This is the output that fires when msg.payload.analyze is set to false.
Now configure it to set the property msg.payload.note to “this is not being analyzed”.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_A34D5EC1416CEDD5473BE8E9F9E9E5AE14C849B2D75C0F81D0E3FB11C060CF2B_1541958372549_change1.PNG)


 When you receive a message that the switch node sends on the 2nd output, it will be modified to contain a “note” element with the string “this is not being analyzed”. If you deploy and test the flow by sending the MQTT message from HiveMQ, you’ll see the output as shown in this figure.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_A34D5EC1416CEDD5473BE8E9F9E9E5AE14C849B2D75C0F81D0E3FB11C060CF2B_1541958488282_change2.PNG)


