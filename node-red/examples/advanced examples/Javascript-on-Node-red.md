# Javascript on Node-red
To write javascript on Node-red, you need to get into the Node-red address first. 
After running Node-red, connect these three nodes as the following picture: 


![](https://d2mxuefqeaa7sj.cloudfront.net/s_27D9C7FD5E92A0B54F0204CD0B7E521A307D7F0384A6455185FEA5FA7E3F775D_1541931541444_Screen+Shot+2561-11-11+at+17.18.44.png)


There are three types of variable, beside “var”, are:
context: use in the flow individually. To connect from one function to another function, use “flow”. It will get the output from one to the other. To use output from a flow to another flow, use “global”. 
For more understanding, follow the examples below. 
This is explaining how context works.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_27D9C7FD5E92A0B54F0204CD0B7E521A307D7F0384A6455185FEA5FA7E3F775D_1541946807204_Screen+Shot+2561-11-11+at+21.31.07.png)


create the node connections as above. Then copy and paste the code below. 
for *count* function: 

value = context.get('count')||0;
value++;
context.set('count',value);
return{payload:value};

for *payload : context.get(count)* :

return {payload:context.get('count')};

After that, you can try clicking the inject(the blue one) and see how it works. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_27D9C7FD5E92A0B54F0204CD0B7E521A307D7F0384A6455185FEA5FA7E3F775D_1541947069948_Screen+Shot+2561-11-11+at+21.37.28.png)


For the second one, you will get: 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_27D9C7FD5E92A0B54F0204CD0B7E521A307D7F0384A6455185FEA5FA7E3F775D_1541947109496_Screen+Shot+2561-11-11+at+21.37.40.png)


Because it is used context , so the second function cannot get the output of the first one to show. 
Let’s try changing context flow. 

value = flow.get('count')||0;
value++;
flow.set('count',value);
return{payload:value};

and 

return {payload:flow.get('count')};

after that, you will be able to get the output of count to show on the output of second function.
This “flow” is only works with function within the same flow (flow diagram on Node-red). If you want to interact it with the other, just using global instead of flow.  

