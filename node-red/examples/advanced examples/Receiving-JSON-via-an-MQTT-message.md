# Receiving JSON via an MQTT message
To use the mqtt node, you need to have access to a broker. There are a number of free MQTT servers running, for example http://test.mosquitto.org/.  Using the broker address and the topic causing it to generate a new message whenever new data is published on that topic. The message will contain information on the published data, including the data itself in msg.payload and the MQTT broker topic in msg.topic.
First, drag and drop an mqtt input node and configure it for the broker. Don’t forget to configure the topic to something unique, in the case of this example we are using noderedlecture/sensor but you should use your own unique topic, i.e. <your name here>/sensor.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0A39ED7A292F0F5C8F2BDDB98DC2F06D07433CDB30BB2875B819CF6094567DAB_1541953636983_MQTTj.PNG)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0A39ED7A292F0F5C8F2BDDB98DC2F06D07433CDB30BB2875B819CF6094567DAB_1541953796515_MQTTJS.PNG)


You can use their websockets client showcase the mqtt dashboard or your own library. You’ll be using their websocket client in this example, so navigate to that page and connect to the broker. You will publish a JSON encoded string to the topic you configured to see both the use of the mqtt node and the json node.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0A39ED7A292F0F5C8F2BDDB98DC2F06D07433CDB30BB2875B819CF6094567DAB_1541953721060_MQTTjso.PNG)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0A39ED7A292F0F5C8F2BDDB98DC2F06D07433CDB30BB2875B819CF6094567DAB_1541953725500_mqttjson.PNG)


Since you are sending a JSON string, you will need to parse the message that the mqtt node generates when it receives the MQTT message. To do that, you’ll need to drag and drop a json node and connect it to the mqtt node’s output. Node-RED’s json node is a sort of convenience function, in that it parses the incoming message and tries to convert it to/from JSON. So if you send it a JSON string, it will convert it to a JavaScript object, and vice versa. If you wire up the usual debug node to the json node and deploy, then use the HiveMQ dashboard to send the JSON string {“analyze”:false, “value”:10} 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0A39ED7A292F0F5C8F2BDDB98DC2F06D07433CDB30BB2875B819CF6094567DAB_1541953804952_mqttcon.PNG)


 If you look closely at the output, you can see that the msg.payload contains an object, which itself has two fields, analyze and value, each with their own values. As you saw in lecture 2, you can access these fields via msg.payload.analyze and msg.payload.value. Let’s take a look at a node that can do that.

