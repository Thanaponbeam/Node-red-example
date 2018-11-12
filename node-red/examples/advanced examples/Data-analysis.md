# Data analysis
In Node-red, we can easily parse the data from JavaScript to JSON or vice versa, by using JSON node. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_12B7F8F1E681AAFCCCFF00409AE72D1367A834B5B24A750DAE765505B4036BA1_1541950764912_Screen+Shot+2561-11-11+at+22.39.10.png)


For example: You get a raw data from sensor, then, you can use JSON node and function node together to get your output easier to read. 
Copy and paste the following JSON data to inject node by select payload type to JSON. 

    {
        "glossary": {
            "title": "example glossary",
                    "GlossDiv": {
                "title": "S",
                            "GlossList": {
                    "GlossEntry": {
                        "ID": "SGML",
                                            "SortAs": "SGML",
                                            "GlossTerm": "Standard Generalized Markup Language",
                                            "Acronym": "SGML",
                                            "Abbrev": "ISO 8879:1986",
                                            "GlossDef": {
                            "para": "A meta-markup language, used to create markup languages such as DocBook.",
                                                    "GlossSeeAlso": ["GML", "XML"]
                        },
                                            "GlossSee": "markup"
                    }
                }
            }
        }
    }

Then, connect these nodes as the below picture. 


![](https://d2mxuefqeaa7sj.cloudfront.net/s_12B7F8F1E681AAFCCCFF00409AE72D1367A834B5B24A750DAE765505B4036BA1_1541951874201_Screen+Shot+2561-11-11+at+22.56.29.png)


When you click on the inject node, you will get 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_12B7F8F1E681AAFCCCFF00409AE72D1367A834B5B24A750DAE765505B4036BA1_1541951939671_Screen+Shot+2561-11-11+at+22.58.24.png)


on the output using JSON. Because JSON node is used to change raw data to JSON type. Since the data  we are giving is already a JSON type, so it shows the same thing. 
 
 On the other output, you will get

![](https://d2mxuefqeaa7sj.cloudfront.net/s_12B7F8F1E681AAFCCCFF00409AE72D1367A834B5B24A750DAE765505B4036BA1_1541952061849_Screen+Shot+2561-11-11+at+22.58.48.png)


 The payload is arrange in Objects not in string. 

