# Sending TCP requests.
 This example shows you how to send TCP requests using the tcp node. In this case you will make an HTTP request following the specifications in ([http://tools.ietf.org/html/rfc2616#section-5.1.2](https://www.google.com/url?q=http://tools.ietf.org/html/rfc2616%23section-5.1.2&sa=D&usg=AFQjCNHYqv4S1C_mL5zvEGplDxt9Z1U67g)).
This example shows the use of the tcp node. It could equally be configured with the udp or http nodes in a similar manner.
 To get started, let’s connect an inject, function, tcp request, and debug nodes

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-21.jpg)


 Edit the first function node to add a function that sets the string “GET / HTTP/1.1\r\n\r\nHost: [www.google.com](https://www.google.com/url?q=http://www.google.com&sa=D&usg=AFQjCNEKlLLbxFSDzP5DEI_kQ-oraaTnUg)” as payload.
 This string is a standard HTTP request, indicating it is a GET request, the protocol is HTTP 1.1 and the host is [www.google.com](https://www.google.com/url?q=http://www.google.com&sa=D&usg=AFQjCNEKlLLbxFSDzP5DEI_kQ-oraaTnUg). The \r\n\r\n is two return/newline pairs which is required in the HTTP protocol.

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-22.jpg)


 Configure the tcp request node to connect to the [www.google.com](https://www.google.com/url?q=http://www.google.com&sa=D&usg=AFQjCNEKlLLbxFSDzP5DEI_kQ-oraaTnUg) server, on port 80. Configure it to close the connection after 1 second (1000 ms).

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-23.jpg)


 The tcp request node response is a buffer and needs to be parsed. Configure the second function node to parse the tcp request node response.

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-24.jpg)


 If you deploy the flow and click on inject, you will make a request to Google and will get a TCP response. The debug node will print the response as a string.

![](http://noderedguide.com/wp-content/uploads/2015/11/Node-RED-Lecture-3-Basic-nodes-and-flows-25.jpg)


 Some of you may be wondering why you need to use a function node to build the HTTP request that we sent over TCP. Why not just use the inject node to input the string? The reason is that the inject node ‘escapes’ the string it uses, causing the return/newline you inserted to be removed. This in turn confuses the receiving server (Google) into not returning a response as it waits for the missing return/newlines. So instead, you build the string in a function node. This is one of those ‘gotchas’ that trips up even experienced Node-RED programmers, so always read the info pane for nodes to make sure you understand any limitations or constraints.

