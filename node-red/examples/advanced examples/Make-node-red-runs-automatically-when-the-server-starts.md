# Make node-red runs automatically when the server starts 
First of all, all you need is to create a new file named **node-red.service** 
or you can run the command below directly, it will create a file for you. 


    sudo nano /etc/systemd/system/node-red.service


copy and paste the code below to directory. 


    [Unit]
    Description=Node-RED
    After=syslog.target network.target
    
    [Service]
    ExecStart=/usr/local/bin/node-red-pi --max-old-space-size=128 -v
    Restart=on-failure
    KillSignal=SIGINT
    
    # log output to syslog as 'node-red'
    SyslogIdentifier=node-red
    StandardOutput=syslog
    
    # non-root user to run as
    WorkingDirectory=/home/USER/
    User=USER
    Group=USER
    
    [Install]
    WantedBy=multi-user.target

Replace USER to your username. My case, username is embedded. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_D6A1069135B2AD04B6BBEB0E15B53A51F296E1352D47E22ECC3E872570B4DFCF_1541923822369_Screen+Shot+2561-11-11+at+15.10.05.png)


After that, run the following commands:


    sudo systemctl enable node-red


    sudo systemctl start node-red

For stopping node-red service: 


    sudo systemctl stop node-red


source: https://diyprojects.io/node-red-installation-configuration-ubuntu-16-04-lts/#.W-ffUKeB1N0


