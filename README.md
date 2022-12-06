# All_about_RP4

##การแชร์ Raspberry Pi ให้เป็น server ด้วย internet บ้าน

บางผู้ให้บริการปล่อย IP public มาให้กับผู้ใช้ ผู้ใช้สามารถนำมาใช้เป็น IP address ให้กับ Server ได้ 
แต่เนื่องจากเป็น IP แบบ Dynamic กล่าวคือหมายเลข IP ที่ได้รับจะเปลี่ยนไปเรื่อยๆ ไม่สามารถกำหนดให้คงที่ตลอดไปได้ 
จำเป็นต้องมีการกำหนดชื่อเครื่องเพื่อเรียกใช้งาน อาจใช้บริการ NoIP ในการจดทะเบียนชื่อ หรือจะจดโดเมนเนมกับผู้ให้บริการก็ได้ ซึ่งก็จะเก็บค่าบริการเป็นรายปี ราคาขึ้นอยู่กับโดเมนที่จด 
เช่น .com ก็จะมีราคาสูงกว่า .xyz เป็นต้น   เมื่อมีชื่อแล้วก็จะต้องทำการ update หมายเลข IP ที่จะใช้กับชื่อโดเมน กรณีเน็ตบ้านจะต้องคอยอับเดทเมื่อมีการเปลี่ยนแปลงหมายเลข ip 
โปรแกรม ddclient เป็นทางเลือกที่นำมาใช้กับ Raspberry 
การติดตั้ง ddclient บน Raspberry ทำได้โดยใช้คำสั่ง

      sudo apt update
      sudo apt install ddclient
      

จากนั้นแก้ไขสคริปด้วยคำสั่ง

      sudo nano /etc/ddclient.conf


แล้วใส่ข้อความดังนี้ 


      ssl=yes
      use=web, web=https://dynamicdns.park-your-domain.com/getip
      protocol=googledomains
      login=username
      password=userpassword
      hostname.domain.name
      



โดยที่ username และ password ได้มาจากผู้ให้บริการ dns
และ  hostname.domain.name คือชื่อโดเมนเนมที่เราจดทะเบียนไว้ เช่น www.example.com เป็นต้น



<img src="https://github.com/Tawan-Phurat/All_about_RP4/blob/main/pics/ddnsconfig.png" alt="script of clientddns" style="height: 300px; width:300px;"/>
