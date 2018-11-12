# Using an mqtt output node to test the flow
 As an alternative to using the HiveMQ test page to publish on the MQTT topic, we can configure an mqtt output node. This is the mirror of the mqtt input node and allows you to configure an MQTT service and the topic you are publishing on. You can then send the node messages with the exact same JSON string we’ve been sending via the HiveMQ test page. Drag and drop three inject nodes and an mqtt output node.

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-16.jpg)


 You can now test the flow you created to analyze the MQTT message directly from the workspace by clicking on the three inject nodes in sequence. The first will exercise the part of the flow handling the case when analysis is turned off; the 2nd two messages will cause the path with the rbe node to be exercised.

