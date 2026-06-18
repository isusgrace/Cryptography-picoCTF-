Hi, Can you speak Thai ?

Yes, I can speak Thai.

มา วันนี้เราจะมาทำข้อ substitution0 หมวด Cryptography

# Step 1 เปิดไฟล์

ข้อนี้จะมีไฟล์ .txt มาให้ ให้เราทำการเปิดไฟล์ที่ไหนก็ได้ อย่างของฉันเปิดใน Notepad

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f36b26c2-ba41-45b3-86b7-82bc3beb4be8" />

ภาพที่ 1

จะเห็นสิ่งที่อยู่ในไฟล์ ดังภาพที่ 1

```
ZGSOCXPQUYHMILERVTBWNAFJDK 

Qctcnrel Mcptzlo ztebc, fuwq z ptzac zlo bwzwcmd zut, zlo gtenpqw ic wqc gccwmc
xtei z pmzbb szbc ul fqusq uw fzb clsmebco. Uw fzb z gcznwuxnm bsztzgzcnb, zlo, zw
wqzw wuic, nlhlefl we lzwntzmubwb—ex sentbc z ptczw rtukc ul z bsuclwuxus reulw
ex aucf. Wqctc fctc wfe tenlo gmzsh brewb lczt elc cjwtciuwd ex wqc gzsh, zlo z
melp elc lczt wqc ewqct. Wqc bszmcb fctc cjsccoulpmd qzto zlo pmebbd, fuwq zmm wqc
zrrcztzlsc ex gntlubqco pemo. Wqc fcupqw ex wqc ulbcsw fzb actd tcizthzgmc, zlo,
wzhulp zmm wqulpb ulwe selbuoctzwuel, U senmo qztomd gmzic Ynruwct xet qub eruluel
tcbrcswulp uw.

Wqc xmzp ub: ruseSWX{5NG5717N710L_3A0MN710L_357GX9XX}
```

นี่คือข้อความที่ถูกเข้ารหัส

# Step 2 quipquip 

เปิดเว็บนี้

```
https://quipqiup.com/
```

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2ada2092-88bb-4ca2-8345-a7d202f92d0f" />

ภาพที่ 2

เอาข้อความที่ถูกเข้ารหัสใส่ลงในช่อง Puzzle จากนั้นกด Solve

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/edaaf9f9-f442-4a16-9942-0d24fcbfd733" />

ภาพที่ 3

จะได้ผลลัพธ์ดังภาพที่ 3 Flag ออกแล้ว

## อธิบาย

quipquip คือ เครื่องที่ช่วยถอดรหัสประเภท Simple Substitution Cipher (แทนที่ตัวอักษร)

หลักการของ Simple Substitution Cipher คือ การนำตัวอักษรทุกตัวในข้อความต้นฉบับมา แทนที่ด้วยตัวอักษรอื่นอย่างถาวร ตามกฎหรือคีย์ที่กำหนดไว้ล่วงหน้า ตัวอย่างเช่น ถ้ากำหนดให้ A=V ก็ให้ A=V ตลอด

คำใบ้ข้อนี้อยู่ตรง "ZGSOCXPQUYHMILERVTBWNAFJDK" เมื่อนำมาเทียบกับตัวอักษร A-Z แบบเรียงกัน จะได้ดังนี้

```
Z=A, G=B, S=C, O=D, C=E, X=F, P=G, Q=H, U=I, Y=J, H=K, M=L, I=M, L=N, E=O, R=P, V=Q, T=R, B=S, W=T, N=U, A=V, F=W, J=X, D=Y, K=Z 
```

เรามาสังเกตตรงบรรทัดนี้ "ruseSWX{5NG5717N710L_3A0MN710L_357GX9XX}" เทียบตัวอักษร 5 ตัวแรก จะได้ "ruseSWX=picoCTF" ในส่วนของพิมพ์ใหญ่และพิมพ์เล็กให้ดูจากในไฟล์ที่โจทย์ให้มา ถ้าเขาพิมพ์เล็กเราก็พิมพ์เล็ก ถ้าเขาพิมพ์ใหญ่เราก็พิมพ์ใหญ่ ส่วนตัวเลขที่คงไว้อย่างนั้น เพียงเท่านี้ Flag ก็ออกแล้ว แต่ถ้าให้ถอดทีละตัว...กว่าจะจบ เหนื่อยลากไส้แน่นอน เพราะฉะนั้น เราจึงเอา quipquip มาช่วยในการถอดรหัส ไม่ถึง 10 วินาที ก็ได้ Flag แล้ว
