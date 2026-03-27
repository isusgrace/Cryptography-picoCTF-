Hi, Can you speak Thai ?

Yes, I can speak Thai.

มา วันนี้เราจะมาทำข้อ StegoRSA หมวด Forensics

# Step 1 สร้าง Directory

คำสั่ง mkdir สำหรับสร้างไดเรกทอรี (หรือโฟลเดอร์) ใหม่บนระบบไฟล์
```
mkdir <new directory>
```
ตามด้วย คำสั่ง cd ใช้สำหรับเปลี่ยนไดเรกทอรีหรือโฟลเดอร์ปัจจุบันในเทอร์มินัล
```
cd <new directory>
```
ตามด้วย คำสั่ง wget ใช้สำหรับดาวน์โหลดไฟล์จากอินเทอร์เน็ตโดยตรงผ่านบรรทัดคำสั่ง
```
┌──(kali㉿kali)-[~]
└─$ mkdir isusgrace02 
                                                                                             
┌──(kali㉿kali)-[~]
└─$ cd isusgrace02

┌──(kali㉿kali)-[~/isusgrace02]
└─$ wget https://challenge-files.picoctf.net/c_plain_mesa/857696a027f6c65f47cf7b8c910430903e7db36e8c9ee183277ad76fa11292dc/image.jpg
--2026-03-27 08:59:08--  https://challenge-files.picoctf.net/c_plain_mesa/857696a027f6c65f47cf7b8c910430903e7db36e8c9ee183277ad76fa11292dc/image.jpg
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 18.239.134.106, 18.239.134.58, 18.239.134.85, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.239.134.106|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20794 (20K) [application/octet-stream]
Saving to: ‘image.jpg’

image.jpg                   100%[==========================================>]  20.31K  --.-KB/s    in 0.001s  

2026-03-27 08:59:09 (36.4 MB/s) - ‘image.jpg’ saved [20794/20794]

┌──(kali㉿kali)-[~/isusgrace02]
└─$ wget https://challenge-files.picoctf.net/c_plain_mesa/857696a027f6c65f47cf7b8c910430903e7db36e8c9ee183277ad76fa11292dc/flag.enc 
--2026-03-27 09:03:12--  https://challenge-files.picoctf.net/c_plain_mesa/857696a027f6c65f47cf7b8c910430903e7db36e8c9ee183277ad76fa11292dc/flag.enc
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 18.239.134.58, 18.239.134.126, 18.239.134.106, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.239.134.58|:443... failed: Connection refused.
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.239.134.126|:443... failed: Connection refused.
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.239.134.106|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 256 [application/octet-stream]
Saving to: ‘flag.enc’

flag.enc                    100%[==========================================>]     256  --.-KB/s    in 0s      

2026-03-27 09:03:13 (207 MB/s) - ‘flag.enc’ saved [256/256]
```

# Step 2 ถอดรหัส

<img width="1920" height="855" alt="StegRSA01" src="https://github.com/user-attachments/assets/efcb2641-df07-4b3a-9d34-504b61b076a4" />

ภาพที่ 1

เข้า CyberChef แล้วเลือก "From Hex" เท่านี้ เราก็ได้ข้อมูล private key มาแล้ว

# Step 3 vi 

คำสั่ง vi เราจะใช้สำหรับใช้สร้างไฟล์และแก้ไขไฟล์ พิมพ์ข้อมูลเสร็จ กด Esc -> พิมพ์ :wq -> กด Enter
```
┌──(kali㉿kali)-[~/isusgrace02]
└─$ vi code02.pem
```

# Step 4 openssl

OpenSSL คือ ชุดเครื่องมือบรรทัดคำสั่งแบบโอเพนซอร์สที่ใช้จัดการเกี่ยวกับระบบความปลอดภัย SSL กับ TLS หน้าที่ของมันคือ...
1. ใช้สร้างไฟล์ CSR เพื่อขอใบรับรองจากผู้ให้บริการ หรือสร้าง Self-signed certificate ไว้ใช้ทดสอบภายใน
2. ใช้เข้ารหัสและถอดรหัสข้อมูล
3. สร้างและจัดการคู่กุญแจ Public Key และ Private Key

อธิบายคำสั่งที่ใช้

openssl: เรียกใช้งานโปรแกรม OpenSSL
rsautl: บอกให้ OpenSSL ใช้เครื่องมือสำหรับจัดการโครงสร้าง RSA
-decrypt: ระบุว่าเราต้องการถอดรหัส (แต่อย่าถอดใจจากเรานะคับเบบี๋ จุ๊ฟม๊วฟ)
-inkey code02.pem: บอกโปรแกรมว่ากุญแจที่จะใช้ไขคือไฟล์ชื่อ code02.pem
-in flag.enc: ระบุไฟล์ต้นทางที่ถูกเข้ารหัสไว้ ในที่นี้คือไฟล์ชื่อ flag.enc
```
┌──(kali㉿kali)-[~/Downloads/mygit/challenge]
└─$ openssl rsautl -decrypt -inkey code02.pem -in flag.enc 
The command rsautl was deprecated in version 3.0. Use 'pkeyutl' instead.
picoCTF{XXXXX}
```
XXXXX ไม่ใช่ flag นะ คือปิดไว้ จะได้ทำเอง
