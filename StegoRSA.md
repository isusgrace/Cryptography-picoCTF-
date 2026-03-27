Hi, Can you speak Thai ?

Yes, I can speak Thai.

มา วันนี้เราจะมาทำข้อ StegoRSA หมวด Cryptography

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

# Step 2 ExifTool 

ExifTool เป็นเครื่องมือที่ใช้อ่าน เขียน และแก้ไขข้อมูล Metadata ในส่วนของข้อนี้ เราจะใช้คำสั่ง exiftool อ่านข้อมูลที่ซ่อนอยู่ในไฟล์

```
┌──(kali㉿kali)-[~/Downloads/mygit]
└─$ exiftool image.jpg                                    
ExifTool Version Number         : 13.10
File Name                       : image.jpg
Directory                       : .
File Size                       : 21 kB
File Modification Date/Time     : 2026:02:07 10:26:36-05:00
File Access Date/Time           : 2026:03:27 10:15:41-04:00
File Inode Change Date/Time     : 2026:03:27 10:15:41-04:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : 2d2d2d2d2d424547494e2050524956415445204b45592d2d2d2d2d0a4d494945766749424144414e42676b71686b6947397730424151454641415343424b67776767536b41674541416f49424151445942674148797171517a4f58430a756c364f752f4a6e4443353454357852776e2b6b4e33384d6d6d46396f2b4f4b344f34387a4946664942572b4f324f7a3772476d38464b51556f6c6d6c4d592f0a504f586a547a302f4b4b594b5062754a33323249574d31414176426d6b6d6c7a52753644325464396a6f525a3164497045444365356a7275394949463247364b0a3139356456684b63674b3475726b4e416b4b6556682b2b35625876424b69746235713863754344776e735044644f36524b58324472587943374f6f50487272700a546153397341736d467142555675416b5553737148367833496548774b752f5a446939445257323436524a54557a6b482b38466f4c6e41564f554c33666435650a7477335a494c364b3141672f4d41346d61694f397576392b6d4557414851513475592f46436b472b326a6f61425342696d6434414f5266684f693344626230540a574264566748376841674d42414145436767454144507968323359504e6d4b79454b6950677864596d3649316144745a6759634f305553616c3074763731756e0a4a43415242482f544b6f444a57396b5354625338736f5639776a4a4c457a736746726a4b6c5956373044427065494845394c5646586f6f2f7079437947776d440a374565734d736f67456c5462507a4d6142676a556b6e58792f71373967747854793359754e71686b4f4b744b4258474a70702f58716c633864635a6e70326c740a506b673134684e394b492f434831753635616235764b7a2b392b704a4161325464466e506b68346d303333536d6a375a785476563877546555634f5347694d6a0a32526b6a55705252655150696a4341464c75646363306b4a42727a6c4d634c574f6e72464d5a755a33366274486158707644757371556272654b6775302f67590a533356415454584734356a2b6b706d72475551356878324d744141766d5869365141453569764a654d514b4267514478587a6730415a784b67545371624464420a334f624f2f726e3571646c7966756449485548663748746678387a437a46627278525a664d73577732366170756e795435317a69494e616d386e66426e4e54760a6b4333654930554439373744502f67357455487544416339646d74754844796b4e376d6d496470376b51387a70777764484a7851477353344639684e5572316e0a394f4f783178524e46724a637a686348634f764a3963316930514b426751446c48594a72744577534a514770764d36304f48556f6f3631386874644c3678694f0a577755547a63616f4e7a2b783070516a6658634357424a4c2b542b536a36486352496d574265644142394a4b6d38724465782b4e4a483939354949526f3149610a47654c435a67492f69685761534334564331796144683138716e6c2f4d537030473476366a393235653476666c7945316e4d6b6e6d6a32786c4e5451596a5a730a4b68587954724f2f45514b42675144506154396d6b5375346169625465344a514f6e36727951414f706747512f6250497144742f4c44736f4a7779784a39355a0a5931624348324c3567775a494f315070314a7067526b2b747a685653626d34634867304d49637167696a65476d475735555353435a6875696d5376667871766c0a675730716356544a636646614e575758626f707a32307a48314e57755044632b4b5a57767346356c6a2b646445457542765773676450513077514b42674662520a6f64517956416b6b494d637a46706a514e415563554f63354b57684a513972647673544d577854764b7147316a42454f774151525834324f6533714d467565690a795167695949697737677a376b42415848644f63477675586c586f646930543876694b774350594f327a5446575544384e7a4468584763624b6b4c36584833320a326b6f754c66545654694742345547786b634143414a4c454e5168707a766d5a3051737171343468416f4742414f6b4732794a68626534683367335531576c6b0a376871516e6147313763673041382b33696e3130466e6568725751426c427659734e655045525a737454784d5169456c464c76354d436a52666d6a6d2b534a500a4b34674d2f6c5567656f4e58435a577a314c333447745538387774374e57366a2b586d6265794e6c34764662776f757a515449303172486876786d6e2b716d710a2b487575432f67396a415369583272303338524b595367780a2d2d2d2d2d454e442050524956415445204b45592d2d2d2d2d0a
Image Width                     : 512
Image Height                    : 512
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 512x512
Megapixels                      : 0.262
```

สังเกตตรง Comment มันถูกเข้ารหัสด้วย Hex อยู่

# Step 3 ถอดรหัส

<img width="1920" height="855" alt="StegRSA01" src="https://github.com/user-attachments/assets/efcb2641-df07-4b3a-9d34-504b61b076a4" />

ภาพที่ 1

เข้า CyberChef แล้วเลือก "From Hex" เท่านี้ เราก็ได้ข้อมูล private key มาแล้ว

# Step 4 vi 

คำสั่ง vi เราจะใช้สำหรับใช้สร้างไฟล์และแก้ไขไฟล์ พิมพ์ข้อมูลเสร็จ กด Esc -> พิมพ์ :wq -> กด Enter
```
┌──(kali㉿kali)-[~/isusgrace02]
└─$ vi code02.pem
```

# Step 5 openssl

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
