# North Project 🥂 🍼 🍻 
 MQTT (MQ Telemetry Transport) เป็นโปโตคอลที่ใช้ในการสื่อสารใน Application Layer ตาม OSI Model โดยรันบน TCP/IP 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_7D0CA30CC88959FB2B0F95EF13CF5241C7BF4D8F9E442680680E95E9C9D684C3_1547114617674_image.png)


สำหรับข้อดีของเจ้า MQTT คือมันถูกออกแบบมาให้รับส่งข้อมูลที่มีน้ำหนักเบามากเหมาะสมกับอุปกรณ์ต้นทาง ปลายทางที่ใช้พลังงานน้อยๆ ส่งได้ไกลๆ โดยใช้งานแบนด์วิดธ์อย่างมีประสิทธิภาพ และที่สำคัญมัน open source คราบ ไม่เสียค่าใช้จ่ายใดๆเลย

MQTT จะแบ่งออกมาเป็น 2 ส่วนด้วยกันคือ 

**Broker**
ทำหน้าที่เป็นตัวกลางในการรับส่งข้อมูลระหว่าง Client โดยมีวิธีการสร้างเส้นทาง (Routing) ด้วยหัวข้อ (Topic) โดยที่ Client ต้องทำการ Subscribe ใน Topic ที่ตัวเองต้องการ จากนั้น Broker ก็จะส่งข้อมูลทั้งหมดที่ถูก Publish ใน Topic นั้นๆให้ โดยที่ Client สื่อสารกันโดยที่ไม่รู้จักกัน ซึ่งถือเป็นข้อดีเมื่อต้องการขยายเครือข่ายก็สามารถดำเนินการได้ง่าย

![à¸à¸¥à¸à¸²à¸£à¸à¹à¸à¸«à¸²à¸£à¸¹à¸à¸ à¸²à¸à¸ªà¸³à¸«à¸£à¸±à¸ mqtt broker](https://pagefaultblog.files.wordpress.com/2017/02/mqtt.png?w=371&h=223)


และหน้าที่ที่สำคัญมากอีกอย่างของ broker คือรักษาความปลอดภัยของเครือข่าย เช่น การทำ Authorization และ Authentication ของ Client


**Client**
เป็นได้ทั้ง Publisher หรือ Subscriber หรือ Publisher/Subscriber ในเวลาเดียวกัน ตัว Client จะต้องเป็นอุปกรณ์ที่สามารถรัน MQTT Client Library บน TCP/IP ได้ ซึ่งตัว Library เองจะมีขนาดเล็ก ติดตั้งง่าย ใช้ได้กับอุปกรณ์ที่มีทรัพยากรจำกัด เพราะการใช้โมเดล Publisher/Subscriber นั้นหน้าที่คิดคำนวณจะถูกผลักไปยัง Broker

![à¸à¸¥à¸à¸²à¸£à¸à¹à¸à¸«à¸²à¸£à¸¹à¸à¸ à¸²à¸à¸ªà¸³à¸«à¸£à¸±à¸ mqtt client broker](https://www.hivemq.com/img/blog/connect-flow.gif)


Client จำเป็นที่จะต้องเปิดการเชื่อมต่อ TCP/IP ใว้ตลอดเวลาเพื่อที่ Broker จะสามารถส่งข้อมูลมาให้ได้ หากการเชื่อมต่อมีปัญหา Broker ก็จะเก็บข้อมูลนั้นใว้จนกว่า Client จะกลับมาออนไลน์อีกรอบ

**MQTT open source** ที่เปิดให้ใช้บริการมีด้วยกันหลายตัวด้วยกันเช่น

![à¸à¸¥à¸à¸²à¸£à¸à¹à¸à¸«à¸²à¸£à¸¹à¸à¸ à¸²à¸à¸ªà¸³à¸«à¸£à¸±à¸ mqtt mosquitto](https://mosquitto.org/images/mosquitto-text-side-28.png)




## ติดตั้ง Mosquitto MQTT Broker ลงบน Raspberrypi

คำสั่งที่ใช้ในการติดตั้งคือ

    pi@raspberry:~ $ sudo apt update
    pi@raspberry:~ $ sudo apt install -y mosquitto mosquitto-clients

กดตกลงเพื่อเป็นการติดตั้ง Mosquitto MQTT

    pi@raspberry:~ $ sudo systemctl enable mosquitto.service

ตรวจสอบการติดตั้ง MQTT โดย

    pi@raspberry:~ $ mosquitto -v

จะเห็นvision ของmqtt ที่เราติดตั้ง
สามารถตรวจสอบIPที่raspberryPI web server กำลังทำงานได้โดยใช้คำสั่ง

    pi@raspberry:~ $ hostname -I


## การตรวจสอบการทำงานของ MQTT broker 

โดยจะทำการติดตั้งMQTT Cliants ลงบน raspberry PI เพื่อทดสอบการทำงานโดยจะใช้คำสั่ง

    pi@raspberry:~ $ sudo apt-get install mosquitto-clients

กดyเพื่อติดตั้ง แล้วรัน Mosquitto ที่พื้นหลังโดยใช้คำสั่ง

    pi@raspberry:~ $ mosquitto -d

**Subscribing to testTopic Topic**
โดยจะรันแยกหน้าต่างกันโดยจะใช้คำสั่ง

    pi@raspberry:~ $ mosquitto_sub -d -t testTopic

สั่ง **“Hello World!” เป็นข้อความเพื่อทดสอบ testTopic Topic โดยจะรันในหน้าต่าง#2**

    pi@raspberry:~ $ mosquitto_pub -d -t testTopic -m "Hello world!"

จะเห็นผลลัพ......................................................................................................
**ทดสอบการส่งข้อความจากหลายcliants** 
โดยจะรันคำสั่งข้างล่างในหน้าต่างที่ #3

    pi@raspberry:~ $ mosquitto_sub -d -t testTopic

แลในหน้าต่าง#2รัน

    pi@raspberry:~ $ mosquitto_pub -d -t testTopic -m "Hello world!"

