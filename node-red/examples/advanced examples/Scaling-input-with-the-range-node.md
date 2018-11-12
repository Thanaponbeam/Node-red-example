 # Scaling input with the range node
 When dealing with real world input from sensors and other devices, an ability to scale input data is often required. Node-RED provides the scale node to support this and allows you to scale (linearly) an input value. Let’s assume you want to scale your value (originally in the range 0-10) to a range (0-255) when you aren’t doing any analysis. This means we are dealing with the lower part of the flow fired when the switch node evaluates the Analyze property as false. To do this, select the change node you configured above (set msg.payload) and copy it with ctrl+c, then ctrl+v. Attach a range node

![](https://d2mxuefqeaa7sj.cloudfront.net/s_8DF93D949D1611628A4B07F36660E5F597C547686E618186D9274375C0D83FB8_1541968081672_range.PNG)


 Double-click on it, and configure it to map the input from 0-10 to 0-255

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-14.jpg)


 The scale node has three options set by the action field. The default will scale according to the mapping given but will happily scale values outside the given ranges, using the same mapping. Scale and limit to target range means that the result will never be outside the range specified within the result range. A third option, Scale and wrap within the target range means that the result will essentially be a “modulo-style” wrap-around within the result range.
Then return to the HiveMQ test page and post {“analyze”:false, “value”:10} as a new MQTT message to the same topic.
 If you return to your Node-RED window, you will see that the debug node associated with the lower part of the flow has fired, showing that the msg.payload.value property that you set as 10 when you published it to MQTT, has been scaled up 255 

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-15.jpg)


