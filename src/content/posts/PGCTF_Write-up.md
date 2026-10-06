---
title: PGCTF Write-up
published: 2026-03-09
description: 網路解謎向的CTF
tags: [CTF, 資安]
category: 網路安全
draft: false
---

這個題目把幾乎所有的THJCC題目結合到了一起，我覺得比較像網路解密
因為沒看過這種一環扣一環的CTF，只有在網路解密看過

喔對了如果你也想解檔案[在這](https://file.pg72.tw/share/-ui1zDOk)
## Part 1
在這個部分，檔案要用頻譜圖開
因為我沒記錯的話提示是"how to see the sound?"和"0:14~0:17"
我這裡用Audacity看
右鍵音軌-頻譜圖
會看到一個網址
![image](https://hackmd.io/_uploads/rkyJAZ2Fbe.png)
`092598.xyz`
直接連上是rickroll
那可能代表要用whois看
:::spoiler
```bash
C:\Users\User\Downloads\SysinternalsSuite>whois 092598.xyz

Whois v1.21 - Domain information lookup
Copyright (C) 2005-2019 Mark Russinovich
Sysinternals - www.sysinternals.com

Connecting to XYZ.whois-servers.net...

WHOIS Server: whois.gandi.net
Registrar URL: http://www.gandi.net/
Updated Date: 2026-03-01T15:08:21.0Z
Creation Date: 2026-03-01T15:08:20.0Z
Registry Expiry Date: 2027-03-01T23:59:59.0Z
Registrar: Gandi SAS
Registrar IANA ID: 81
Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
Name Server: ANITA.NS.CLOUDFLARE.COM
Name Server: MICHAEL.NS.CLOUDFLARE.COM
DNSSEC: unsigned
Registrar Abuse Contact Email: abuse@support.gandi.net
Registrar Abuse Contact Phone: +33.170377661
URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of WHOIS database: 2026-03-09T09:10:52.0Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

>>> IMPORTANT INFORMATION ABOUT THE DEPLOYMENT OF RDAP: please visit
https://www.centralnicregistry.com/support/information/rdap <<<

The registration data available in this service is limited. Additional
data may be available at https://lookup.icann.org

The Whois and RDAP services are provided by CentralNic, and contain
information pertaining to Internet domain names registered by our
our customers. By using this service you are agreeing (1) not to use any
information presented here for any purpose other than determining
ownership of domain names, (2) not to store or reproduce this data in
any way, (3) not to use any high-volume, automated, electronic processes
to obtain data from this service. Abuse of this service is monitored and
actions in contravention of these terms will result in being permanently
blacklisted. All data is (c) CentralNic Ltd (https://www.centralnicregistry.com)

Access to the Whois and RDAP services is rate limited. For more
information, visit https://centralnicregistry.com/policies/whois-guidance.

Connecting to whois.gandi.net...

WHOIS Server: whois.gandi.net
Registrar URL: http://www.gandi.net
Updated Date: 2026-03-01T15:26:16Z
Creation Date: 2026-03-01T14:08:20Z
Registrar Registration Expiration Date: 2027-03-01T23:59:59Z
Registrar: GANDI SAS
Registrar IANA ID: 81
Registrar Abuse Contact Email: abuse@support.gandi.net
Registrar Abuse Contact Phone: +33.170377661
Reseller:
Domain Status: clientTransferProhibited http://www.icann.org/epp#clientTransferProhibited
Domain Status: serverTransferProhibited http://www.icann.org/epp#serverTransferProhibited
Domain Status:
Domain Status:
Domain Status:
Registry Registrant ID:
Registrant Name: gugu gaga
Registrant Organization: A Fake Company
Registrant Street: No.404 Fake St.
Registrant City: No have this city
Registrant State/Province:
Registrant Postal Code: 123
Registrant Country: TW
Registrant Phone: +886.900000000
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: gugugaga980925@gmail.com
Registry Admin ID:
Admin Name: gugu gaga
Admin Organization: A Fake Company
Admin Street: No.404 Fake St.
Admin City: No have this city
Admin State/Province:
Admin Postal Code: 123
Admin Country: TW
Admin Phone: +886.900000000
Admin Phone Ext:
Admin Fax:
Admin Fax Ext:
Admin Email: gugugaga980925@gmail.com
Registry Tech ID:
Tech Name: gugu gaga
Tech Organization: A Fake Company
Tech Street: No.404 Fake St.
Tech City: No have this city
Tech State/Province:
Tech Postal Code: 123
Tech Country: TW
Tech Phone: +886.900000000
Tech Phone Ext:
Tech Fax:
Tech Fax Ext:
Tech Email: gugugaga980925@gmail.com
Name Server: ANITA.NS.CLOUDFLARE.COM
Name Server: MICHAEL.NS.CLOUDFLARE.COM
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
DNSSEC: Unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2026-03-09T09:10:52Z <<<

For more information on Whois status codes, please visit
https://www.icann.org/epp

Reseller Email:
Reseller URL:

Personal data access and use are governed by French law, any use for the purpose of unsolicited mass commercial advertising as well as any mass or automated inquiries (for any intent other than the registration or modification of a domain name) are strictly forbidden. Copy of whole or part of our database without Gandi's endorsement is strictly forbidden.
A dispute over the ownership of a domain name may be subject to the alternate procedure established by the Registry in question or brought before the courts.
For additional information, please contact us via the following form:
 https://www.gandi.net/support/contacter/mail/


Domain Name: 092598.xyz
Registry Domain ID: D627460974-CNIC
Registrar WHOIS Server: whois.gandi.net
Registrar URL: http://www.gandi.net
Updated Date: 2026-03-01T15:26:16Z
Creation Date: 2026-03-01T14:08:20Z
Registrar Registration Expiration Date: 2027-03-01T23:59:59Z
Registrar: GANDI SAS
Registrar IANA ID: 81
Registrar Abuse Contact Email: abuse@support.gandi.net
Registrar Abuse Contact Phone: +33.170377661
Reseller:
Domain Status: clientTransferProhibited http://www.icann.org/epp#clientTransferProhibited
Domain Status: serverTransferProhibited http://www.icann.org/epp#serverTransferProhibited
Domain Status:
Domain Status:
Domain Status:
Registry Registrant ID:
Registrant Name: gugu gaga
Registrant Organization: A Fake Company
Registrant Street: No.404 Fake St.
Registrant City: No have this city
Registrant State/Province:
Registrant Postal Code: 123
Registrant Country: TW
Registrant Phone: +886.900000000
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: gugugaga980925@gmail.com
Registry Admin ID:
Admin Name: gugu gaga
Admin Organization: A Fake Company
Admin Street: No.404 Fake St.
Admin City: No have this city
Admin State/Province:
Admin Postal Code: 123
Admin Country: TW
Admin Phone: +886.900000000
Admin Phone Ext:
Admin Fax:
Admin Fax Ext:
Admin Email: gugugaga980925@gmail.com
Registry Tech ID:
Tech Name: gugu gaga
Tech Organization: A Fake Company
Tech Street: No.404 Fake St.
Tech City: No have this city
Tech State/Province:
Tech Postal Code: 123
Tech Country: TW
Tech Phone: +886.900000000
Tech Phone Ext:
Tech Fax:
Tech Fax Ext:
Tech Email: gugugaga980925@gmail.com
Name Server: ANITA.NS.CLOUDFLARE.COM
Name Server: MICHAEL.NS.CLOUDFLARE.COM
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
Name Server:
DNSSEC: Unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2026-03-09T09:10:52Z <<<

For more information on Whois status codes, please visit
https://www.icann.org/epp

Reseller Email:
Reseller URL:

Personal data access and use are governed by French law, any use for the purpose of unsolicited mass commercial advertising as well as any mass or automated inquiries (for any intent other than the registration or modification of a domain name) are strictly forbidden. Copy of whole or part of our database without Gandi's endorsement is strictly forbidden.
A dispute over the ownership of a domain name may be subject to the alternate procedure established by the Registry in question or brought before the courts.
For additional information, please contact us via the following form:
 https://www.gandi.net/support/contacter/mail/
```
:::
其中有個東西是gugugaga980925@gmail.com
![image](https://hackmd.io/_uploads/BkGZJzhK-l.png)
但不可能是gmail
所以把後面去掉這樣去找
![image](https://hackmd.io/_uploads/HyRmyM2FWx.png)
果然發現怪東西
點進去會看到打亂的QRCode和一張圖片
![image](https://hackmd.io/_uploads/HJz_kfnFbg.png)
下載下來嘗試拼回去
![image](https://hackmd.io/_uploads/H1O4ZMhYbe.png)
試過很多次掃不到
![image](https://hackmd.io/_uploads/HJQRVM3Fbl.png)
後來去問了PG說他掃的到(????)
也是成功拿到連結了
![image](https://hackmd.io/_uploads/Bkn5IzhYZg.png)
https://file.pg72.tw/share/xK0UUwmt
打開來有密碼
![image](https://hackmd.io/_uploads/HyK4vzhYZe.png)

回到IG最下面的貼文說密碼是照片裡學校的簡稱
![image](https://hackmd.io/_uploads/HyG1Pfhtbx.png)
丟給AI看看
![image](https://hackmd.io/_uploads/HyXxtfhtbl.png)
嗯...我去他IG找找線索好了
嗯?![image](https://hackmd.io/_uploads/B1GUKz3YWl.png)
`AHSNCCU`?
不會是密碼吧?!


![image](https://hackmd.io/_uploads/SJgYtMhFWe.png)
還真的是lol
下載檔案下來
內容是
```
0110/110/1010/1/0010/{/011/11111/011/_/001/_/000/11111/0100/0001/00011/100/_/011111/1/_
```
我選擇丟給Ai解
![image](https://hackmd.io/_uploads/ryDzqM2Fbl.png)
![image](https://hackmd.io/_uploads/r1l3f5MnYWe.png)
好拿到第一部份的flag了
:::success
```
PGCTF{W0W_U_S0LV3D_1T_
```
:::
## Part 2
把後面的SSTV解碼出來
![image](https://hackmd.io/_uploads/By_6iMnKbx.png)
會出現這些東西
```
++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>------------------..>-----------------.--.<..>----------.+++++++++++.<..>+.----------.<..>--.++.<..>++++++++++.--.<..>++..<..>--------.+++++++++++.<..>---------------.++.<..>++++++++++.------------.<..>++++.+++++++++++.<..>---.++++++++++++++++++++++.<..>----------------------.+++++++++++++++++++++.<..+++++++++++++++++++++++.+++++++++++.<++++++++++++++++++++++..>---.+++.<..>---------------.+++.<..>+++++++++..<..>.<+++++++++++++.
```
我直接丟給AI跑
![image](https://hackmd.io/_uploads/BJZqhMhtZx.png)
感覺這是base64:`44SQ44GR44SI44GI44SQ44SS44KV44GI44SG44KV44Si44Sh44KV44SV44GJ44SS44SA`
![image](https://hackmd.io/_uploads/SJk9aG2Ybx.png)
是，然後翻一下我當初弄得
https://hackmd.io/@nihs-zackzheng/Hkc06f3Ybg
接下來最後這個結果我覺得還有加密
再看一下是不是凱薩(只有凱薩才有移位)
![image](https://hackmd.io/_uploads/rJ9aRzhFWg.png)
好第二階段也出來了
:::success
```
r3p0rt_0n_dc_w1th
```
:::
為什麼不是c3a0ce?因為前後文是連貫的
## Part 3
這個部份我用hex查看器看了這個wav
![image](https://hackmd.io/_uploads/SJtGeX2tWl.png)
尾段有點怪東西，讓我改看看副檔名然後解開
![image](https://hackmd.io/_uploads/BkURgmnt-l.png)
man! what can i say
然後不出意外就出意外了
![image](https://hackmd.io/_uploads/SygdbmhKbl.png)
![image](https://hackmd.io/_uploads/BkN_Z73YZe.png)
這下不用破解xslx的密碼了(本來是有密碼的)，只要剛剛unzip檔案名稱來解出下載連接的密碼
密碼就是`password`
![image](https://hackmd.io/_uploads/HJEWGmnY-l.png)
下載下來點開
![image](https://hackmd.io/_uploads/SyIzGQ3Ybl.png)
這就是wav壓縮包的壓縮包密碼了
![image](https://hackmd.io/_uploads/rkIwMXhF-l.png)
然後打開是一個ai的鏈結https://gemini.google.com/gem/1mpG1EMZRX6dfyoUgumQZlcImO_mHZsWQ?usp=sharing
嘗試把我們要的東西騙出來
![image](https://hackmd.io/_uploads/rJ6hfQhtZx.png)
好騙出一個怪東西`YTLINK{x5W8qMbaiEQ}`了
那看看會連到什麼東西
![image](https://hackmd.io/_uploads/r1oemm3Kbe.png)



<iframe width="560" height="315" src="https://www.youtube.com/embed/x5W8qMbaiEQ?si=fKLNXcZCTT-XYx4X" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>



接下來就是看影片
光看看不出所以然來，看看有沒有什麼其他的東西
先下載下來
裡面好像有藏文字
![image](https://hackmd.io/_uploads/BJeyLXhKbx.png)
![image](https://hackmd.io/_uploads/SyNEUQ2F-g.png)
![image](https://hackmd.io/_uploads/SkjHI7htZx.png)

-------------
把所有找到
會是
:::success
```
_scr33n_and_wp}
```
:::

## 合併&提交
把所有東西合併起來
會是`PGCTF{WOW_U_SOLV3D_1T_r3p0rt_0n_dc_w1th_scr33n_and_wp}`
丟到ctf.pg72.tw
![image](https://hackmd.io/_uploads/HkTZvQnKWg.png)
送出!
![image](https://hackmd.io/_uploads/BypSw7ntZg.png)
耶~
## 後記與感謝
反正昨天才解出來
![image](https://hackmd.io/_uploads/B1DPvQnKZl.png)
這就是我
然後感謝出題PG讓我解那麼精彩的題目
感謝草莓糖在上上週一起陪我解出Part2
感謝Gemini幫我decode和找圖片位置


最後感謝所有人看到這，最後留個base64
```
Q1RGIDFzIG15IDFpdmUh
```
這裡就正式結束了
