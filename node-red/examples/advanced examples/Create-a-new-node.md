# Create a new node:
First of all you need to create a folder “node-red-contrib-demo” (any name you like) 
using command 

      *mkdir node-red-contrib-demo*

Then, create a file package.json by using command 

      *touch package.json*

using *sudo nano package.json* then paste this code there and save. 
**{**
    **"name"         : "node-red-contrib-demo",**
    **"version"      : "0.0.1",**
    **"description"  : "A sample node for node-red",**
    **"dependencies":** **{**
    **},**
    **"keywords": [ "node-red"** **],**
    **"node-red"     :** **{**
        **"nodes":** **{**
            **"sample": "demoNodes/HelloWorld.js"**
        **}**
    **}**
**}**
Create another folder inside node-red-contrib-demo. Let's name it demoNodes. 

      *mkdir demoNodes*

Go to this folder and Create two files: HelloWorld.html using *touch HelloWorld.html* then *sudo nano HelloWorld.html* paste the code.


    <script type="text/javascript">
        RED.nodes.registerType('Hello World',{
            category: 'Demo',
            color: '#ffaaaa',
            defaults: {
                name: {value:""}
            },
            inputs:1,
            outputs:1,
            icon: "face.png",
            label: function() {
                return this.name||"Hello World";
            }
        });
    </script>
    
    <script type="text/x-red" data-template-name="Hello World">
        <div class="form-row">
            <label for="node-input-name"><i class="icon-tag"></i> Name</label>
            <input type="text" id="node-input-name" placeholder="Name">
        </div>
        <div class="form-row">
            <label for="node-input-topic"><i class="icon-tag"></i> Topic</label>
            <input type="text" id="node-input-topic" placeholder="Topic">
        </div>
    </script>
    �
    <script type="text/x-red" data-help-name="Hello World">
        <p>A node that increments every time a new message is received and sends Hello World in return.<br/>
        </p>
    </script>

*touch HelloWorld.js* then *sudo nano HelloWorld.js*


    module.exports = function(RED) {
        function helloWorld(config) {
            RED.nodes.createNode(this,config);
            var context = this.context();
            var node = this;
            this.on('input', function(msg) {
    
            var outMsg = {payload: "Hello World"};
        
            node.send(outMsg);
            
            });
        }
        RED.nodes.registerType("Hello World",helloWorld);
    };

Then run the following commands: 
 go to home/user
 then   *cd node-red-contrib-demo* 

     *sudo npm link*
    *cd /usr/lib/node_modules/*  
    (check if there is a folder”node-red-contrib-demo” we created or not)
    *cd node-red*
    *npm link node-red-contrib-demo*
    *node-red restart*

Go to Node-red address to see the new node we created. 

    
    

