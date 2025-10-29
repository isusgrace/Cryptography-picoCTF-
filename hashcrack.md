Hi, Can you speak Thai ?

Yes, I can speak Thai.

มา วันนี้เราจะมาทำข้อ hashcrack หมวด Cryptography

Step 1 สร้าง Directory

คำสั่ง mkdir สำหรับสร้างไดเรกทอรี (หรือโฟลเดอร์) ใหม่บนระบบไฟล์
```
mkdir <new directory>
```
ตามด้วย คำสั่ง cd ใช้สำหรับเปลี่ยนไดเรกทอรีหรือโฟลเดอร์ปัจจุบันในเทอร์มินัล
```
cd <new directory>
```
```
┌──(kali㉿kali)-[~]
└─$ mkdir isusgrace02   
                                                                                             
┌──(kali㉿kali)-[~]
└─$ cd isusgrace02
```

Step 2 MD5 cracker
```
https://crackstation.net/
```
ข้อความข้างต้นเป็นเว็บไซต์สำหรับ crack

MD5 Cracker คือโปรแกรมหรือเครื่องมือที่ใช้ในการพยายามหาข้อความต้นฉบับ เช่น รหัสผ่าน จากค่าแฮช MD5 ที่ได้จากการเข้ารหัส

สำหรับข้อนี้ โจทย์จะให้ netcat มา เราคัดลอกแล้ววางใน kali ได้เลย
```
┌──(kali㉿kali)-[~/isusgrace02]
└─$ nc verbal-sleep.picoctf.net 12345
Welcome!! Looking For the Secret?

We have identified a hash: 482c811da5d5b4bc6d497ffa98491e38
Enter the password for identified hash: password123
Correct! You've cracked the MD5 hash with no secret found!

Flag is yet to be revealed!! Crack this hash: b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
Enter the password for the identified hash: letmein
Correct! You've cracked the SHA-1 hash with no secret found!

Almost there!! Crack this hash: 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
Enter the password for the identified hash: qwerty098
Correct! You've cracked the SHA-256 hash with a secret found. 
The flag is: picoCTF{XXXXX}
```
พอมันให้ค่า hash มา เราก็เอาไปเข้าเว็บไซต์ที่ฉันแปะไว้ จากนั้นกด ✓ I'm not a robot แล้วดูตรง Result เอาสิ่งที่ปรากฏใน result มาใส่ใน "Enter the password for identified hash: " ทำแบบนี้ไปเรื่อย ๆ จนกว่า flag จะออกมา

XXXXX ไม่ใช่ flag นะ คือปิดไว้ จะได้ทำเอง

อธิบาย nc verbal-sleep.picoctf.net 12345
ส่วนที่ 1 nc ย่อมาจาก Netcat เป็นเครื่องมือเครือข่ายอเนกประสงค์ที่ใช้สำหรับอ่านและเขียนข้อมูลข้ามการเชื่อมต่อเครือข่ายโดยใช้โปรโตคอล TCP หรือ UDP มันมักถูกเรียกว่า "มีดพับของแฮกเกอร์" เพราะสามารถใช้ได้หลากหลาย เช่น ตรรวจสอบพอร์ต เชื่อมต่อไปยังพอร์ตของเซิร์ฟเวอร์ เป็นต้น 
ส่วนที่ 2 verbal-sleep.picoctf.net นี่คือชื่อโฮสต์หรือที่อยู่ของเซิร์ฟเวอร์ที่คุณต้องการเชื่อมต่อ "คุณ" ในที่นี้เป็นบุคคลที่กำลังใช้คอมพิวเตอร์และพิมพ์คำสั่งเพื่อเชื่อมต่อไปยังเซิร์ฟเวอร์ที่ผู้ออกโจทย์ได้ตั้งไว้ ผู้ออกโจทย์มีบทบาทในการสร้างและจัดการเซิร์ฟเวอร์ที่ชื่อ verbal-sleep.picoctf.net แต่ไม่ใช่ผู้ที่กำลังพยายามเชื่อมต่อด้วยคำสั่งนี้
ส่วนที่ 3 12345 นี่คือหมายเลขพอร์ตที่โจทย์นั้น ๆ ทำงานอยู่บนเซิร์ฟเวอร์ การเชื่อมต่อจะเกิดขึ้นบนพอร์ตนี้ ซึ่งหมายความว่าคุณกำลังสื่อสารกับโปรแกรมหรือบริการเฉพาะที่รันอยู่บนพอร์ต 12345 บนเซิร์ฟเวอร์ verbal-sleep.picoctf.net

เพิ่มเติม
- 12345 ไม่ใช่หมายเลขพอร์ตที่ฉันได้ หมายเลขพอร์ตที่ทุกคนได้จะไม่เหมือนกัน ฉันจึงปลอมแปลงมันเพื่อป้องกันความสับสนของผู้ที่เข้ามาอ่าน write up ของฉัน
