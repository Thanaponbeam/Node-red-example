# Using the rbe (report by exception) node
 In this example, you’ll continue your message analysis theme and add nodes to the part of the flow that is used when you determine that the flow should be analyzed. You’ll be using the rbe (report by exception) node which only passes on data if it has changed. You can set it to examine a message payload and either block until a message changes (rbe mode) or when a messages changes by a specified amount (deadband mode). In rbe mode, it works on numbers and strings. In deadband mode, it works on numbers only and uses the configured deadband as a + or – ‘band’, so that the incoming value can fluctuate within a range before it fires. Adding in another change node which you’ll connect to output 1 of the switch node. You’ll then connect an rbe node to the switch node. connect a change node, and an rbe node like this. To remind us that this output deals with the flag “analyze”, add a comment node and write “Analyze = true”. Comments are useful when writing complex flows.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_47435894B0E0C94E31A42726CDCDA8E6EB42C6D0C189A386988D438A6F2B35EC_1541967669687_rbe2.PNG)


 Edit the change node to set the msg.payload to msg.payload.value. This will set the output of this node to the value found in the msg.payload.value element of the input received 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_47435894B0E0C94E31A42726CDCDA8E6EB42C6D0C189A386988D438A6F2B35EC_1541967705941_rbe1.PNG)


 Since you want to determine if this value has changed by 20% or more, you’ll need to double-click on the rbe node and configure it to block unless the value changes by more than 20%.

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-11.jpg)


 To test the flow, deploy this flow and then return to the HiveMQ page and send a series of messages. Firstly, you’ll need to set the analyze value to true so that the switch node sends through a message on output 1. If you use the original message value of 6, this will fail to pass the rbe node. If you then send a second message of value 10, the rbe node will evaluate the difference between 6 and 10, see it is greater than 20%, and send on a message to the final debug node which will print on the debug pane

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-12.jpg)


