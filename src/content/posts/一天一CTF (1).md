---
title: 一天一CTF
published: 2025-12-29
description: 一天一個CTF，持續努力!
tags: [CTF, 資安]
category: 網路安全
draft: false
---


> 第一步是你必須說：「我辦得到」 — 威爾.史密斯
> 
> 二十年後，你會懊悔更多的是那些現在沒做，而不是真的做了的事。所以，拋開繩結，駛離安全的港灣。掌握好你的風向，勇敢的探險，夢想，發現吧。 -馬克．吐溫
## Day1 2025/11/3-picoCTF Flag in Flame
![image](https://hackmd.io/_uploads/HyW0lM8ybx.png)
先解開base64
![image](https://hackmd.io/_uploads/BkS7NMI1Wg.png)
得到這張圖片
![image](https://hackmd.io/_uploads/H1HkXzIk-e.png)
> 很重的ai味

然後~~辛苦的~~丟給ai解碼![image](https://hackmd.io/_uploads/H1bv7MUk-x.png)
flag就有拉
```
picoCTF{forensics_analysis_is_amazing_c75dd08e}
```
![image](https://hackmd.io/_uploads/S14rVf8kbl.png)

## Day2 2025/11/4-picoCTF Inspect HTML

![image](https://hackmd.io/_uploads/SkqQLdDkbg.png)
首先打開網站
![image](https://hackmd.io/_uploads/BkqIUdvJWx.png)
然後右鍵-"檢查"
![image](https://hackmd.io/_uploads/Hksv8OP1Wg.png)
把`<body>`展開
![image](https://hackmd.io/_uploads/Hk9tUdwk-g.png)
![image](https://hackmd.io/_uploads/B1DhL_P1Zx.png)
now we get flag!
右鍵flag-copy-Copy element

![image](https://hackmd.io/_uploads/S1CAL_D1Zg.png)
(記得去掉!--和-->)
`picoCTF{1n5p3t0r_0f_h7ml_1fd8425b}`
![image](https://hackmd.io/_uploads/HyvO_tD1bl.png)

> 最近都先挑簡單的先做
> 我怕我做太難的會爆

## Day3 2025/11/5-picoCTF DISKO 1

![image](https://hackmd.io/_uploads/BJyTXau1be.png)

先點[here](https://artifacts.picoctf.net/c/537/disko-1.dd.gz)下載檔案
![image](https://hackmd.io/_uploads/rk6pQaOJbe.png)
打開之後發現檔案是.dd檔
![image](https://hackmd.io/_uploads/BkE_Np_J-g.png)
在這邊卡很久，直到看到了[這篇文章](https://0xodinx.medium.com/picoctf-disko-1-writeup-2730afc8f0be)
![image](https://hackmd.io/_uploads/HJv1JCOyZl.png)
行，我試試看
打開kali虛擬機，把檔案傳過去(或用wget下載，用gzip解壓縮
`wget https://artifacts.picoctf.net/c/537/disko-1.dd.gz`
`gunzip disko-1.dd.gz `)
先切到放檔案的目錄下
![image](https://hackmd.io/_uploads/ByDEy0Oy-l.png)
確認一下檔案類型
![image](https://hackmd.io/_uploads/Hyq_10O1-l.png)

然後直接讀字串
![image](https://hackmd.io/_uploads/BJTZg0ukWe.png)
get the flag!
`picoCTF{1t5_ju5t_4_5tr1n9_be6031da}`
![image](https://hackmd.io/_uploads/r1MZW0uybe.png)

> 炫耀下桌布btw
> ![image](https://hackmd.io/_uploads/HkQYxAd1bg.png)
> ![image](https://hackmd.io/_uploads/BJQhxRdyZg.png)

## Day4 2025/11/6-picoCTF Log Hunt
![image](https://hackmd.io/_uploads/Bk4OX19Jbe.png)
先把log下載下來打開
第一行就發現有flag的一部份
![image](https://hackmd.io/_uploads/HkZ3rk51Zx.png)
這就代表說有`INFO FLAGPART`就是flag會出現的地方
按下Ctrl+f把INFO FLAGPART貼進去找(或丟到linux用`cat server.log| grep "INFO FLAGPART"`)
我用linux抓出來了這些字串:
```bash
┌──(kali㉿kali)-[~/Desktop]
└─$ cat server.log| grep "INFO FLAGPAR"
[1990-08-09 10:00:10] INFO FLAGPART: picoCTF{us3_
[1990-08-09 10:02:55] INFO FLAGPART: y0urlinux_
[1990-08-09 10:05:54] INFO FLAGPART: sk1lls_
[1990-08-09 10:05:55] INFO FLAGPART: sk1lls_
[1990-08-09 10:10:54] INFO FLAGPART: cedfa5fb}
[1990-08-09 10:10:58] INFO FLAGPART: cedfa5fb}
[1990-08-09 10:11:06] INFO FLAGPART: cedfa5fb}
[1990-08-09 11:04:27] INFO FLAGPART: picoCTF{us3_
[1990-08-09 11:04:29] INFO FLAGPART: picoCTF{us3_
[1990-08-09 11:04:37] INFO FLAGPART: picoCTF{us3_
[1990-08-09 11:09:16] INFO FLAGPART: y0urlinux_
[1990-08-09 11:09:19] INFO FLAGPART: y0urlinux_
[1990-08-09 11:12:40] INFO FLAGPART: sk1lls_
[1990-08-09 11:12:45] INFO FLAGPART: sk1lls_
[1990-08-09 11:16:58] INFO FLAGPART: cedfa5fb}
[1990-08-09 11:16:59] INFO FLAGPART: cedfa5fb}
[1990-08-09 11:17:00] INFO FLAGPART: cedfa5fb}
[1990-08-09 12:19:23] INFO FLAGPART: picoCTF{us3_
[1990-08-09 12:19:29] INFO FLAGPART: picoCTF{us3_
[1990-08-09 12:19:32] INFO FLAGPART: picoCTF{us3_
[1990-08-09 12:23:43] INFO FLAGPART: y0urlinux_
[1990-08-09 12:23:45] INFO FLAGPART: y0urlinux_
[1990-08-09 12:23:53] INFO FLAGPART: y0urlinux_
[1990-08-09 12:25:32] INFO FLAGPART: sk1lls_
[1990-08-09 12:28:45] INFO FLAGPART: cedfa5fb}
[1990-08-09 12:28:49] INFO FLAGPART: cedfa5fb}
[1990-08-09 12:28:52] INFO FLAGPART: cedfa5fb}
```
再把flag依照出現順序拼出來
Get The Flag!
```
picoCTF{us3_y0urlinux_sk1lls_cedfa5fb}
```
![image](https://hackmd.io/_uploads/HyV29y9JZx.png)
## Day4 2025/11/6-picoCTF Vigenere
> 忽然想多做一個

![image](https://hackmd.io/_uploads/HJG4QWckWg.png)
`cipher.txt`:
```
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}
```
已知key為`CYLAB`
那就用線上工具解密!

我使用[ctf.bugku.com的解密工具](https://ctf.bugku.com/tool/vigenere)來解密
![image](https://hackmd.io/_uploads/rJKkVWqyWx.png)
解密之後就有flag啦
![image](https://hackmd.io/_uploads/rJvHV-51Zx.png)
```
picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_d85729g7}
```
![image](https://hackmd.io/_uploads/Hk084W91Wx.png)

## Day4 2025/11/6-picoCTF Vigenere
> 忽然又想多做一個

![image](https://hackmd.io/_uploads/BkxCF-cybx.png)

`readmycert.csr`:
```
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF81YWVi
MGQ0Zn0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAMCkf11rmV8rgqPvC2ZiPA6W+5RfOTwU6u3WpGvLA+2YFzocBPut
aATTxTPB+uaN2ZN3Z5J2CTFGmPzI4sUQfSqhZGuAqbfMyDDR8pRswmIYVJ6s0Apc
Toi7H8m3IShSbeE0pZUSIJpbK1a7V6lJqgwFMDI1qrgNhGgZaMA/l+d2J0vC3EYd
AijwSs8APcp6woWbFGYwdw5KaBsjn23oVz2G4h3/TmdB5g5e6Oq+kgi38NEpRDS0
ylXo9mUko3FqS4I6y9gOtDEI4uZaCJZuXHDmBpqZ04MfXbIVlHjF9NMOjDvXLonN
650oaANBm4bhBlgid0Fx48Z36tbtAVivZEcCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAHZx6h9r
G/SE7RCoX6ndk5BOJprRiHpxOqPLAWcDyKHfStln0/HcQZzIrRVRsmoHiOmch+md
PBA1b+M5aj+3BWtPR9jOY4vht+ZmHAKa0WfQxwb2dBxsRPKTTDea0wN2u8BHLlSM
PbWPNuz+TKySL41xfwFuM4VN/ywn58GTvdb7HXgwNZCGgo2N1WhRq/dBMiagXMah
yb6gX4erugCu61T5tyD80hgsNBjaqyIdy/whRfC/Pmn3QHmdkqB5ZCPezwb2OLm4
5RDGv3WOB5q0BofoUGhVq757QE8qhL3oTvV2WlLoi3YWaZkJMCeR3vnH92cKC1Ov
FxdQuLOH8GMvl7U=
-----END CERTIFICATE REQUEST-----
```
先讓我們知道[什麼是CSR?](https://www.ssl.com/zh-TW/%E5%B8%B8%E8%A6%8B%E5%95%8F%E9%A1%8C/%E4%BB%80%E9%BA%BC%E6%98%AF%E4%BC%81%E6%A5%AD%E7%A4%BE%E6%9C%83%E8%B2%AC%E4%BB%BB/)
我在網路上找到了[這個工具](https://www.ssl.com/zh-TW/csr%E8%A7%A3%E7%A2%BC%E5%99%A8/)
直接把csr的內容貼上去按綠色的就行
![image](https://hackmd.io/_uploads/B1srq-5yWe.png)
flag就在`Common Name`這裡
```
picoCTF{read_mycert_5aeb0d4f}
```
![image](https://hackmd.io/_uploads/r1uC9-9kWe.png)
## Day5 2025/11/7-picoCTF morse-code
![image](https://hackmd.io/_uploads/B1akMMiyZl.png)
[檔案](https://artifacts.picoctf.net/c/79/morse_chal.wav)是個音檔
我直接丟到https://morsecodegenerator.org/tw/morse-audio-translator 上去解
![image](https://hackmd.io/_uploads/ryftNGjyZe.png)
再把所有字改成小寫加上_
`picoCTF{wh47_h47h_90d_w20u9h7}`
![image](https://hackmd.io/_uploads/rJCHHGsyZe.png)
## Day6 2025/11/8-picoCTF caesar
![image](https://hackmd.io/_uploads/Hy00HnnJZl.png)
`data.enc`:
```
picoCTF{mbyccsxqdrobelsmyxigfknnoo}
```
我使用[dcode](https://www.dcode.fr/caesar-cipher)解密
![image](https://hackmd.io/_uploads/ryg-vn2J-x.png)
看到cross的有意義字源我就覺得這是flag
```
picoCTF{crossingtherubiconywvaddee}
```
![image](https://hackmd.io/_uploads/B1OBw2hJ-e.png)
## Day7 2025/11/9-picoCTF rotation
![image](https://hackmd.io/_uploads/S1TdclAk-x.png)
`encrypted.txt`:
```
xqkwKBN{z0bib1wv_l3kzgxb3l_949in1i1}
```
使用[decode](https://www.dcode.fr/rot-cipher)的`Automatic Decryption`功能
![image](https://hackmd.io/_uploads/Hk-bilA1bx.png)
![image](https://hackmd.io/_uploads/HyOZil0kWx.png)
```
picoCTF{r0tat1on_d3crypt3d_949af1a1}
```
![image](https://hackmd.io/_uploads/SJfQjgRJZx.png)
## Day8(Day9補) 2025/11/10(2025/11/11)-picoCTF SSTI1
![image](https://hackmd.io/_uploads/HkbY3jllZe.png)
這個網站要用到[SSTI惡意指令注入](https://www.cloudforce.gamania.com/tw/news_detail?type=technology&id=285)
然後根據網站上的每個指令依次測試
![image](https://hackmd.io/_uploads/r1CLCjgx-e.png)
我在網頁上看到，我覺得可能是這個
試了半天沒出來，所以我查了一下
找到了[外國大佬](https://medium.com/@jojolucky221/picoctf-20250-web-ssti-1-56b85ac6b278)和另一個[佑仔](https://hackmd.io/@YuYutw123/picoCTF_Web?utm_source=preview-mode&utm_medium=rec#SSTI1)的解題筆記
![image](https://hackmd.io/_uploads/rkOPJ3exbl.png)
他們都先使用ls來檢查內容
`{{ config.__class__.__init__.__globals__['os'].popen('ls').read() }}
`
![image](https://hackmd.io/_uploads/Bk15ZhgeZg.png)

然後使用
```
{{ config.__class__.__init__.__globals__['os'].popen('cat flag').read() }}
```
![image](https://hackmd.io/_uploads/Hk2oZ3xxbg.png)
get flag!
```
picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_4675f3fa}
```
![image](https://hackmd.io/_uploads/SJMkG3exZe.png)
## Day 9 2025/11/11-picoCTF Ph4nt0m 1ntrud3r
![image](https://hackmd.io/_uploads/ryXME2ll-g.png)
先下載安裝[wireshark](https://www.wireshark.org/download.html)
打開
file-open
![image](https://hackmd.io/_uploads/BkiJr2lg-g.png)
選擇檔案的路徑
打開會長這樣
![image](https://hackmd.io/_uploads/ByeQIhxlWl.png)
然後呢就爬文
爬到了佬的[文章](https://hackmd.io/GXc9gzpARW6fNj1TtmUqvg?view)
他上面提到用時間排序
因為題目有一個hint是Time is essential
接下來逐個找出來(依據佬的筆記大概從 Time 0.002212 開始會出現 Flag 經過編碼之後的東東)
然後就轉碼
~~flag:`picoCTF{1t_w4snt_th4t_34sy_tbh_4r_e5e8c78d}`~~
> 說實在我根本不會抓包解包
> 阿結果flag是錯的
> 有反轉
> 我找到了[外國人的筆記](https://medium.com/@tolentinojesusanthony/picoctf-forensic-ph4nt0m-1ntrud3r-1d79fed7cf0d)
> 他寫的flag是這個picoCTF{1t_w4snt_th4t_34sy_tbh_4r_f318db22}
> wc?
> 還是錯的?
> 真要我下手啊
>ok我解出來了
>
包從
## Day10(打贏復活賽)2025/12/3-picoCTF repetitions 
![image](https://hackmd.io/_uploads/ByEaXppbbg.png)
![image](https://hackmd.io/_uploads/SyCCXT6ZWx.png)
直接解碼
一直姐
姐到最後的flag
```
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}
```
![image](https://hackmd.io/_uploads/SkeuHa6ZZx.png)



## Day 11 2025/12/18 picoCTF Scan Surprise  掃描驚喜
![image](https://hackmd.io/_uploads/B1cVKUZX-l.png)
`challenge.zip`:
```
C:.
\---home
    \---ctf-player
        \---drop-in
                flag.png
```
`flag.png`:
![flag](https://hackmd.io/_uploads/By7AYU-Qbe.png)
用線上工具掃描
![image](https://hackmd.io/_uploads/HyRy5IbmZx.png)

```
picoCTF{p33k_@_b00_0194a007}
```
![image](https://hackmd.io/_uploads/BJCZ5UZXWl.png)

> 這也能當CTF...

## Day 12 2025/12/19 picoCTF information  資訊
![image](https://hackmd.io/_uploads/BJTVPPz7-g.png)
```cat.jpg```:
![cat](https://hackmd.io/_uploads/SJOiPDfQZl.jpg)
我一開始用Hex工具找(想說可能藏在hex)但沒有
後來用 [Online-Metadata](https://online-metadata.com/zh) 查看元數據發現怪怪的東西...

![image](https://hackmd.io/_uploads/H1c7_vMQbe.png)
這個看起來像Base64(按照picoCTF的~~習慣~~)，但他沒有關鍵的== :cry: 
那就試試看吧
![image](https://hackmd.io/_uploads/Hy8O_wG7-x.png)
是耶
耶拿到flag了
```
picoCTF{the_m3tadata_1s_modified}
```
![image](https://hackmd.io/_uploads/B1TcOwMQ-e.png)
 
## Day 12 2025/12/19 picoCTF Corrupted file  檔案損壞
![image](https://hackmd.io/_uploads/BkGuH_MQbl.png)
這題是看[medium上大佬的文章](https://medium.com/@cozyxss/corrupted-file-picoctf-writeup-1e25eb2bb182)解的
![image](https://hackmd.io/_uploads/BkmVLOzXWl.png)
先使用[hexed](https://hexed.it/) 查看文件的Hex值
![image](https://hackmd.io/_uploads/Sk4C8dzXWx.png)
有一個JFIF，那他頭會是什麼呢\?
會是這些
![image](https://hackmd.io/_uploads/rkTID_f7-l.png)
把它改好![image](https://hackmd.io/_uploads/BkrYDdGmZx.png)
存成jpg
`file (1).jpg`:
![file (1)](https://hackmd.io/_uploads/ByBnDOfXWe.jpg)
```
picoCTF{r3st0r1ng_th3_by73s_2326ca93}
```
![image](https://hackmd.io/_uploads/SkmRPuMXZl.png)

## Day 13 2025/12/20 picoCTF Verify  驗證
![image](https://hackmd.io/_uploads/BkypLQEQWg.png)
先連上伺服器:
![image](https://hackmd.io/_uploads/HJnxw74mWl.png)
然後先使用`ls`看有什麼檔案
![image](https://hackmd.io/_uploads/ryP9vQ47bg.png)
然後 `cd files`
And `ls`
![image](https://hackmd.io/_uploads/HyFxOm4mbx.png)
然後開始驗證sha256`sha256sum 02kLdPvr  3HWGffFE  6JGob933....`
你會得到這張表:
:::spoiler
```
87c3b0d3c1ed24251e37b0751349b306686f2a0251a3faafeb0e901bab96b26a  02kLdPvr
67ca9b396a77d563d66b9158da40f3e4e780e5b244cb65e77722ccc34165a804  3HWGffFE
9d41432c483dd058dcb3f5b3702946a27d5179aeb4fd97b9fb58397ad7b4ce21  6JGob933
e4ad546bc827ece358ef790eb2c4c1a55a08bbbc2cd6c78faa0d822f7c4da3cc  AXwbPGqz
157221d44557474eb5c011f6e85d2b0d41b816483d85bc56d2b49b55582a75ed  F7pJKgt3
a70750f90599268a714fd82a9a910b763db2ece22567b9c3dfde18726c6a58fc  JZuYuOle
63bbed35df199e774e7861d14a5abad3d08f1c2209fc9f896bf97cd5a9a93aae  OgbJmSsl
93d57ad55f4e2b269360de5778c0810778981dee6b17d9b13ccba84546ca9af2  SliwhkVP
1ef57dcac260991397252b5da02efa8f1504494baef9bcd7d23bbc7797f4f88c  XmYppXhk
fda3a83becb1507ae394d918f8d2727f4be3c4b54bf4c83e5bd04b37cb21aea7  bSkjXxrA
6edfd5bb980fee3a9e90219d5d87965d9de3166d6263b40c6ae6b558e378111e  fM4Y8XlN
22d08fe3955ebc370f9019c2453409fbc550c98b20b3a9def85c33fa19f4d7b2  k3Je1oZv
5505c750729ed42de1a87f64b68dffe3d476f9c32aa1cc943e76690755c80009  pbXSC543
b874d11a9a1f8877450b87591deb1b1c4ff080dd2896ca6f7e72acbec9f6fe3c  uVGzmmri
6219489551ec8831730fc42c70abdd04a16776183c44c62fba833943f3645ff0  yRSmctoR
1cceaf56a71d4e73576bef1e02a51263d5b8df747fa547c2d64c9ec6a5ef99dd  0AEMwSHP
38e8f08ab00599f91771494a3476c676463d7e686b2fd978dca699ba548885ad  3KQWpDpt
4fac90376a7d47bad4240067a8ae5eb6f7f00ad4cf02a00bd2e48540d69d66c4  7GdIoG6L
40d8639fcba4cb7e9ee47c9faea81e76f7d4ec6ddc6de8e2010632e8d8eee546  Ae01ONEX
8b8027a9eaae34d31f95ed70fafa9a7012fd5bb488708ed53a9f1b015ad45daf  FA1DL0lH
53583b95b87644073b3f17b3e31846ae68d6f2ea5732f047afeeee452317399a  K4w4LSpK
46039a97d82ed9b22c793a7908cf5f904a2252eb53116283d9c24a2ff8019f41  OvH6KubA
c8b1bea17cc254c984047f98a6943df741ff2077d427587a6c65c9ddaf42e5d1  SuTmtwHT
b4c9eacca6e5f68024521acb56caae4b289d44fd0d310d3d5ac353fa452d5cf7  Y9apvJeb
e7c0a3ed6e9db9c3b3fa856ef0ab4bb4e0bf49b90ae8e3420ab600f992bb4d21  bXmTLFnK
48a4314e1d00be7eff63d4a2fbda29fb479e3698652aac68896ef5b9ce9b922c  frJix6dy
823db2220a03c17f2b37a15b861f667a457e1e25403d9f2d01976aceb3493e84  l4aPZsIN
f787bd5c22e33717f8d90da57e2158032a5df0c43853700ed33b1d94625bbd31  q2mcPs3c
2f71b22c3ac3d84081a92eaf7b59a46a221c3c9899fd252a58fe0699f69ef22d  uiBoxr24
656376aa2c2e825866edc436b89e25ac5a21a8f2861702f3478dcb7691077903  ybQ7iIWc
6606c707cf5d145c738ccc7b5f6a404f40499ef2e3d21c81ce8671d701f06428  0QBK0M73
26b4f4f89ad41f7eb348084add3f9bf7a5baea2500ee47ee57aab7b471d2a233  3RwrWxAh
7ce150de6af51bbb4a19baeb501171ee3564784209bddb336ed29b3b12e3574e  7M36N0ZG
1c9666e507482e499e826d19dd2b7814d4f709325109a28f17196c52b16b252a  AfqV5hAX
f8a39b266528bd3e01ee4ed50d544f49ad819df7275621e6301282c3a293c2ac  FaSiQOUR
641bec9bdb770bda0e92ba713ff5fe32b939ba16417286e95214ea6685325a20  KM1rOvYX
25e2d42de09bac8adb698638756c30412028bf2c4428c2a4dae4e95d10056d75  P0pMREh2
b3a745060d75161684bfe1cbf9bf4ab1a37d73af06867158320bd696241a89f2  TAh3haNF
f7345e10efa04712bc9c097fbf23822eae117f0b037159d6a625bd12ddcebb43  YJZwL09m
4eff44752ec8f15bc425835870e5bd0981592f50e511ebd8911b9decb64977c7  byaxGEzl
c83798cb55b52a3aff7900473a7a7433d0ae4cb42d72ff4173df4acaafdd2e37  fzjMwVlq
8bf76d372095d248547a60658a86e2930827cef380b240c7ca20a19818184ce0  lCWOa2m6
70d1cc2066e5c152412866874e9bac892533a2a89044793aef0969e3b5b791a2  qhTEo0LL
d91b84b4b13b04cb11e2fb03a1a1a35be6e2b5ce10b0b34fc36ac4cc3611c397  urhbGMnd
c2099aa04d7b40bb64227e4fcda991e2b75a71616deda55f7af562b3fbd5c55e  z8QLAIjY
7c18ec256d95af21dbb8aa8b7d72ecaee7debf86892230d9c70c1e122c56d796  0ReLqo7l
497f6e49bb144e85fd61ea03203535e889f931eab00e791f18b5f2ed8039fa4b  3UI1Q3Im
c6652fec5c49fbbf08d0dc26172f9f453941b54bb24fbed3e68726458ae13734  7S05biBB
5bcf0bec2d377659b6bc0293e9d3f708dcde86005418edfa830996fde5723a71  AuXnIN8I
185f93b8ae132b36852afede2d0585c0e202330d007e6d3eadee4a1bca494506  GBMBtUcG
8516450cd8a2c1ed26f15fcdd48ce78e5cf4fa7b10620600ab2bdcfbe6dd901c  KRxkl4ki
3497fc8b0d4ed0570bb7bab0f435255d5822625bfacdf1c9f006e30ff939ae82  PK3nRKAh
8800bd39fbdb26f6e3bbf0bbf67ac5d5ca8527fe5f3c307cbd508ea054c9a031  TIC1KArZ
e5878ad8affaa6cdfeee8c1970fcf6c356d50614eebe103e6ccf148566bc2574  YXeLAbOj
51588d7aef92d2e00a3ba0010bdedbb992984f1d198187d9111ce9733afa9afd  c5K8wpvT
cd14ad97398128bb3f3624b9d81d49ea514f12092eee0f532e5a8f8d8f1518c0  g33i1myO
31beeb9ce36db82f28a4b2f8702fb41e5a36d5399e5e30d236e782435634c532  lY9YUKSk
b2864a8afbfed55f3244572a0940b3888c35d1afba85a19ab4e7f68bbf3e8560  qxtRkCQq
9d8ed791b142d700b470ef60eb19ddbeceae88b1eed9a71a12d7b71214ca79cf  v7gF2ZIR
87ceec22eb23cd8dbe6b727807153c614e14710ee1b86ebf839837410db961bb  zKjekGtU
243a3167ec727432c5c588487848805f88562a459f0f52d8fe5c809b4e3961f8  0pYtGDyN
2b2077661276508f47c2238573c9afba869b7d7afb01252727d8868475d3d0d8  3XFTF7vi
f9684f3b3118811f5c85374b178594831716598e443cc6d477cb169a6a0f05ed  7SXF5dDA
41a5529a5f005c4900ea42581a15a8047969650dda0609b11c5b6586e359c68b  Av9IEmci
e92c298e69e07ca395f7e7871048be6a3e5a89bab1005454ed2dfca91a6de95e  GGpU931s
a6c1f6ccf857d0e503fd8b700292ede9e3988bdebb39288aafc49c0903e0f2d9  KaGA7sxA
27f5073db4545e8df8a3724152cee4cada016a613c8f0d4d328b54c42f16dc7b  PVAhaXhI
dfa5f44af72b450b88589f714b863c56b7e86bace2895f2156010e2ecfa2af69  TJect2dg
569d19491c54d272ffd4298497b5a9770896be6382101109bffd0b73b63eb91f  YmQKA23p
87f32602546e3ee981db881b24135755f16c2dbf740c7a0d83bc3f33be3e7fea  cAehfago
54b08976ea67826a68df7c16e7db1c3b6478351dd7cfac57a2d6bea4b8146cde  gNe3d0tj
2f630fb284aaf5e4f6f52031834b590e71b734c782a82b8d72d88b83c4da2229  lpgH0BeK
7d199d5bd3fbdcc98dcd2ac2aa74b4cd8fd3d20edb85ccb92b130e2c45728125  r0zVMZkQ
22811aaef1d52d627f9d50e0b45cf9ca0f9c3ef119be63074c16ae51110f45ff  vJ3qPWEu
9910658855ed1d8dc29473f860a3442df235593e96d80dda3a51776a4b9ee793  ze9Qihpg
8b17e0e68b9508240a82b7606a9ada765d101e3ccca24a401086a1110f10e936  13eD2Klj
d63f877474df655f49b1d93806c18483f46b39f589135a7ccd623ed88bef296d  3azP1Vr5
455040106290ee3fe07446351d92a12ad684e0c2e6a06ab4cf822481e95bc5b7  7XpL7kA2
7a909ad52a38bde6c28501a6875df0fc38c8b82c8931559729fd36b361768b51  BVQMsUMN
c44f5815aeed931fa385f02b292850b6daf770ad44858c27c55393224c715321  GTH1LeLw
0598c2535e1fc3d03f2c892ff83cd676db8b2dfabd4be6d52f276d4d9bb87f53  Kopd5uAS
e178e47068133e1cc218b9606de9afa3abfbcb09374814f6172c7595b2f9e69c  PbCHfm8l
1a88389eed7357d18148c477dc3565816b1d7449b2a1281d6b323c310e28a3eb  TSGfXer8
dd9c5e8a0d47f17d0c00aa634c66f98eb7b879d12b46825ce6aa71d322c58857  YoOZ5qVn
60d1fb2e4aca2163d76ab396fda4adf23b79269c44dc991fc1c154be85937f2a  cAgx0hQ8
623b335271448a2fac7a26d73a01493a44efc893be975b46b8585df36cec5d8f  h6P0bHfg
91942183eb850b085e52e516399f7e713d805b8afd679934b6802ebe3f6a0afb  lty8luMw
4b829119a9a6232baf41272a35cecde1f6caac339be427fce2789cd308bec36b  raIgZC8T
644d583efc14fc807ebefdf33d64fa6b74991484f8dcae2cb26d560e7886610c  vMdtOisa
6f8ca03d84f8db4348398d4c57736951c28b2872ef6f918cc4aa03bae67dca3d  zfFqIJrW
f60eeacf11219c38754b874863e3364d9a90c854f84972ea03e4bb125276b42c  15s8svF3
e33e177eef2c1a5dd0cae42ea2dbecfb66255c16340259186f055ba618b88418  3bwissRA
328cda47e2de47b32cc4f24f3b4f68172fab527d6d1e5face87fc2799dcf9d13  7ZEsnWZx
2e6bc7379a67c4263a0a7f4bd7dbdab97b4ea565d707807cb708084666032e04  BYWVMQ8G
ae727780ea058767d44fa1fe53053015b2f3d335eb60baaa424e008b5822f5f7  Giagg0HI
e5dc465374749038b2ba5aace9e3081ec6864751bc959d6efc29e535df911f1d  Kqq1CiRK
e6ddc0e9eb7ee9ba0dc207c451b86430d18539cb521296447e0318fa483b391a  PisLwk6C
ebb7493a347527408555b4bbb1993eef74f4b2b10eec578d16fb14d4b338f549  TdeDBXMf
dc9e3ff877eabdc206dbe9f643dc40743ea6aa18f6140e060478a23d7584686b  Yqx2G9d1
933a7b99a8fa56bbff31085ee3d8a460fd0d7c2c1395a14cedfde41560caf15e  cBdFMzZa
0ceaebf53132bb9440f2fb92970ba9c3cec286798f7b7fa5076b172e6777f795  hIbQdK4d
c344491b0eff8a63926953bb298b2ff433e994b171956b902481d15b8f2aade4  mAZwT81W
6b6ee3b30337f0a6b7520c1658c0ad09f3587081eb3d7724d0051bf5a1672b4e  rse22gSC
c029b4109b73350dbb76f7f24bb99ac5345cac5342498d1fc87fb5ae6fa40936  vT94qEUU
c3366a02b371e9e36ef62ecffffafb99d5e6f380a8ff2c2ada684e3e528c5ec2  ziobqxT9
658581c1008cb4debd37045626d2f4533b926ebffbd47bd6debfa93205c2d918  1BX0cysv
fe04a5bb4ebea571df8c206d44f1dfad2634eb0bb112b37afabe104dae8dc270  3llQZxg9
e8010cfb1b4e7823b43e67e66eaf8be3c9f2d72acae9523d35ee9fde81b8a71b  7dnW8EpS
29609f6874e6a0d90f060965236de5316b409e826746abb22a77a27b80875906  Bb0A4ZUF
68f7aa10b412bdc999fe044eda8739a87277c319d08fd329464ae2a7a56aa0f3  Gup9YNYb
c18bffa33042d9fa4f602aae7c90d1b30a1bdb5b76e34edbe06c0ee0bbdf8e5a  MCFq06DD
7044b1bd6f78ad3a0730a3781613f2c6e410637b24a1b5a5ed7f96d5c96c04b8  PucU9ljB
aa1cadfcde7a71b00345bb9d3215deaeec79e00f158fc565cc5984c67c8cd913  Tz1xgD5A
d35fd57e1130601d9c29856cd73b450010f6138f7198e5821b6f4acc39f83d89  YrKlF95C
af7a53031091f89d38c3571060f1dd55617ee71cd6b1d03223845c9d0f24c860  caVHWehf
b96cf609b328b88ab727628fc2b553b517b7f37bc70346977affa67fde226cdd  hueXtQsv
8b69b43addce521765ddccfea37187495eeb84f5f5c8116dc6fe27b4211ff6e7  mL2zl8ME
0cd1e34d4adca3f90d94b2334ebde1e0bc2319b33c98b7556d9a38c7d8cd6e8e  s1T1hXGi
db57334082c1833368719fdda2a899bc8fd1e7a0f3b0d27096ab15e1c4ae4305  vZ9Qc5Cg
1bb3cd55deefe5255c3a9c864853d3ffc7d78fcfa1e80b882636d696129b3015  1QyIAyVK
844e0e8877420c40643077f8eb291bb5df39b0d50481078fec186021435cbdfa  3niXrkT4
ff897449e27281cb7ed245763fa8d73fd8ea0071095d4c250335206c1b43a76e  7e0ugnNi
dc5dbe21ff011357c37f684459719d403602b8a4e86b024464d97618486fd583  BjOuTdvt
c8072cd658d67fbc73e872f577c87c549fb04a25dd35f24d89c42e545d679a71  Gyn3Qful
b1c70e2762730559e1568598f12d7f16c555b06dc86e582c394c52230333bd6c  MRW8xKE7
c03b6a2fbe7c87a5fa9e287cb676a9790ed1e4ed3520e6e3f9cede72627d9f10  PyzlgxBl
74260726b5ab74b1c6102bfb1b0e7b29ef9518a7c5d67131bc59598c79bc2703  U6Za1XXb
a2dba873a39a63ef8bfd29baed73ecb4133036625f9608cdb62615948a7b2d0c  ZS6vNpit
2da7ab6ad6ab342cea8353a75674c2929a4345a80db4f01a93aa15a7db60036c  cbKOHVgV
4f6df4fad9fa0304b32dad472c4c4b7a6ebe127ee4289c95d362d3d0daf3a0dd  i9nzJ3r6
ac5990afaa7d3e7eab00af758c5c159543b49a50b32567954918870b7b177bb6  miUtTQRm
f686a22552f01df89bef392a046ff02123612b26987df9b822f24427d7f26b8e  sHWDCVFR
3a50a8f54cd1f0594458e5fbde64a21560c60b953f83ca1d2f82b809678059cf  vZXXKL7g
7860e56e6f902c36c647e72a368d766ba83ebe61e197d08e2de42bd5b1aa9bb3  1WzFkIC5
a133863c44b8bc0e541cce1b6a5b4de9cabe1b839c5ef8fdceefc6a0697a35fc  4E42FQrx
7826f92b35f443fa95562c127341f5b3c216123c41a7ecf093e706c349cede6e  7enMn1rk
2eb7bee4a425fc3ebe305322319f53e8d677236c0943e0de5af673b00185b639  CDVB02i6
c6e9af17c752fec2492f39c6db1b9635d934c8175760ef775a954c22ced5ee06  HUGRY61E
71983ce7ae526a69631cff37cb6b19de5020184d48163d17887e9ec147903bce  MkEdjeVZ
29f9c223a1d65045492c489d7af46d2b0a5b933094381a1f5ce912772c7f215d  QU8jejZq
54d50b90efd6b0f691e34cbb69d49b48aea034381a8604748c12bf4dd19f3e36  W2hZvcID
0498558d284b804a9c2118343d6c4b303d51c91754a4dba104de8f462a62d6c5  ZS7jkTUt
5cf53330aba9cdd47e7e2f1f3108aac315ee3e45fabf7ba05a4f1af322c5af26  cxjAxbcB
0f55abfccfae087cc5ee957cb73d9cb8b8cb087d0f78984bd8d93bf8c15f8da7  iBekBdEx
8e29227a6dbdcf52e800abf249e97ca8ac4907060f55ecec3cd99f5a3b75faad  nYMkLfqq
c2d13ff8e04507c6276727003de701c035f8961c93cd437ba1eb226db369ddd8  sODASTm7
2a7472392fa03e83a8aaed7382501f298848540fb03e0d56ccd5e7cc9816761a  vlXYHLR4
cf8f82e7e63fb26d6bc8680c4d5c7c46bcbdc3bdc12eec5d717c6062da228687  1fPO7Wz1
542a4fb2057febb1fd47b6737a8f6d238bdc8ce45e114a55e7eb4c7135905725  4RWg3C81
69ce6ee1d62f4ad48451cc6f485c6e0b9f2fa88dac92bfe410844cbac3ac988a  7iM83rpT
b72e7c53024adf52255240e22f3caaad0d8f6c8f6fc2c09f59bfe6fc147371b8  CLcdCN8f
c210b967f2252e448030953a8e49f9addfc7bd4aa2259b06b1e0964be41d714a  HUqcWryv
051fee8919ce25c4af4f15d002890a28c1c02a0797ac83e9f4f5982337bb46b5  MoKJFjOi
b3524a2fc95f1380a6ffb9fd77957a72107b266f52ce2b2e2542e1e40c3c8d00  QUesl6sJ
073f31f0fb7b393f372a1505e5a5735e3e84a18f708305a7fb4e1cec5fe3491e  WJFLBATt
59bbfbdb82686d9f6fce7e47b60955182ba550fc9af841e273dc758f1bf800fc  ZTxbKkJG
9365ad6ec42d57a783ac26f8b3b31caf8b8a3103301dbece418824f34d419b52  d5EQVHHc
5f27354f02e5147c4414cf03ccd428fa94019cfbcf3d22beabc3050bd4455bcf  ia64o1VA
84220611edf0543f583626df269f0b2c561a096eca96567c0ae519123e9516e8  ngS5ThOq
c5833172998cc03ea6e5ccfe6c7ff557f24946b974fca77dba421c6df3732519  sTNxbYIX
b4c4693a6461f521d561a07d60861ce611680a92ae810f9266ef0847086cd35d  vy3RDHxy
ec510cb763998ebe017a5a30c5f89f11eece72a0fa245626a40727ff54d5ab78  1iUcIRwR
881a325685b96bcd76ffbaa48636e97e135199818cd6379a611c42659679f08a  4WsDciyV
9aadbc84cd8e8e5bb5f68ecfbeb873161027f342f15a7239b52b0083cf610d1b  7qVcsxIn
ee4cd7abd9904fad8b12c5b00ab8fa68649df76395e375904a61c51812ef8f61  CfZp4f2N
867bb7ab42225150b6bdb7804536729f8ae0354f0f8ae7ef28fb5cab58c44cfd  HVhGYkYw
1ea4eb8107331a47f0203e8b21815fe4b511a38c662b4ce96b5c5eb1017f6bbe  Mrl2cMHD
f7a715df3fb3bb452c4b8af29a21076bcf0b064198a31b38e5daa040db720588  QjfpcKtL
25affd8eb9271463e13f74cdd63003dce0470a63e6a31229ebdafdd4452cb68d  WLCnFHkD
81a1304a5559dc90f3060350e3253b8ed7844119dcc637de555f80f8eee9b823  ZXWIGnQR
aadda7398725512ac75dc5910a94163fbd29b8a50c4223a9d8c06fa300151265  dGbl67gA
dac515417ac42536a6f2cc09432af3a84662ebd30b574248840ed43caef83814  inbE9V4Z
6319463e65d0a0a102b1582544be4f4504b2e40d4e75d0590cbef669084f7adf  niAMHayw
cbeb404501866928d3e682a583b2611b226976f4ba8b277ffeb229962758ba75  sbuTFkuC
c2cfd10715e0618374fd906cb95ef6d6c21266db7aeb9b2213fe94920758d0f8  wH52POYK
4b970ba0b2be8546d30dc4ca2e77baf3b597cf1d573b4b66f681168572372d77  1kzeT7Bq
dd81f88c10bea4d2602100f63df1608793ccf7261fd6abb8758a0fa3d62555a1  4YmX8P1z
00b971a42827648a63305ce92a18112b199d1043935f4180b155cf6176044563  7x5Qa3WK
52a1324ac1d035c964dc6e5460ed1ef5b5097977e07483df1bac579c3cfe2ad5  D3FjiyXm
8a21cae12874b809cf04540963572624dc2b30535c302e99499d21f1cc092a1a  HkwhoPkp
a33699c4c44f57fed1ffbf54b1bc012c01d0855b5bbb3db1ff138e6c44d0c072  Ms5Mvz12
a8fe7f35be118e6611a07b7f1c62317311dde1d00976783546460fe8100acd9a  QkF8ZdDf
4c05e355e427358eb7ad0c3c3bb487ddbdd62ce4cf27332f5057cf7e8e44db47  WOHDiZ4q
b35084176f9bbf055b5d18a474972b1498d40f87c4e3e94b9e4c21b576146892  a2OU257J
528ba4c7c5c54d43ceff8163fa2d6b57fa4879b4a0c2b94fca9c7e7f1a76cbd9  diVxZXPr
37616b4f4120b3c0b3a2028aab736a32c32a29a45c75a5b4e8c39b3eff48a636  iyKEK5tY
f6c4393b9b4b1463b5426919644228acb53886f12a26a171caa4a0c3830bdc67  np9TOAIR
c8b7aa1ab6096bc03fcb35e4362d9e160dab549efbe1fe2186b107d24d42c066  scPPxxi7
9a31be04105a29887bab62645b8e1e10690db77a606c74d394af5984ad10cf41  wR9DoLPS
8da597f2a97e225f9944e433b98fb7c41fc1004d6f8fa12245eebb94f7e4d65e  1s9fb01L
16f1f957b34292dbbe235f69bcb2930c5ef9cd97958a1b2ac82c74aa4cf8356a  4lpXJyrZ
fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7  87590c24
ae5bc69ebe3d9fb3f478666123383a25471d570e1c1afe4186c1f18d54bc082d  DQlu1oVQ
223542642db77dac29ee7fe5753ee5069730c2d51ec7ae7d0b6e9432e496bbf2  Hw4z4pGA
c2f8faf5292931f4efb8a941ef4000c49d3ace7be47883794fc9df160552c3aa  N36WmSck
f73cd546118e8e5dbd289ebc329ed0ca76bea714a02f20de73b70e3066af28b3  RD85xyJi
774cda7254de090a966573d71bb55449c058dd8dcb484c5e023cc2679e8f09de  WY59WpIg
ce5563451758665b431ecf2a8b4544d1a3359d0cf3b7486f6cb95eb88ca256f4  a5BwxEPT
bd121299ac6a5a5a873779f0c04084fb388ae55e4f31313f16b44f4150f13be1  dmc1Epts
8efc2a80f26e4845f49e6d872ef8b7484bd8b685533bdd85e3bb8149ab69c13f  j21jebUD
c314ddc739e02ab59ec2d01e98c1d9d7fdcd7ce5d99325284f1bdf7b71278a6a  o4p7FB5l
cc7bc1f65f086424d6091c052f7bfe74d738a2d42c9c770de74ccea4593d78a2  srli5tAs
f83a052169e5e576b4a231ebff10638a2f23abe4d8aa12a002f64dcb4feb13e8  whsqK6Xi
e2121b753185be8ca8bc6c04b01c708461946deb637632edcef57c3423116c3a  2EHy0UNu
95a809a1598143a50ba620e9387eff3a03fb378be49e9fd2d1209219cdce5cc5  5L6bCEOe
6600f46e718e227c666cdde6c51bce48a659320dae333a7eece342c4dea32a61  8pMqC98d
df91b40a5085c2836f69bb1b96a6df3402658c256beea530bc983bac5830f2ca  DUx15XmG
62083cbec204552c1d2c8c8c80d8078c49bc50c46e9ab267bb1ff47fc6eb56ce  I7ySGmF3
9dfd2a780eeaf3303ae94e7b7d8ec2d787ac0f8fb381637545be0fa8aa8f6ffe  NTsSRBdP
04dd8f21134d6b29d037172e279f88315104326e7690e1170a9b546725f7b7bc  RGc1b7Dz
40a1d6c6a811809c86053fd74a3605f54fb7d0122c933b85d8d2454096f95ff3  WZcRSCOi
dda2048d594389b16999a6718a6553dde4a327ab9eb27bebf12bda8eb95668c9  aAv6C6d8
f42d3abadec263c8f31c91007471357d318b16d74a01f8fe7d20c908fe17a4f1  dzxHhn9S
fc850738aa461ec041eaa58d5ac7f649413eea4784340d140a72b51e5b675889  jFn9chPx
70f096e8b04163eff93f91c2b61d1e5cc10b4a3622b90f0ec9ef2eb0e81356dd  oNQJCg54
5216c40b2c74beccdab7999a759968f869fd59b1930f280084215396796cc3b2  t1UlIMzc
423f0435ca5567e776ae7e47ca2405861f460f8f3ec348ec12527ac6c7ba9535  wp0CW0xc
cf00202ce2298b01b3bca28c8412d4a0c65f0aa62b2676f495123bfbeaea4c03  2HLMOyNv
cc6df4c1547d8fb811816b2ad327a9bb253e59d93c62aaeb98939017b6645870  5VDBcjMu
32f8e050dfb066f8078f94faae3cc03ed87fa077ebb67cf775c750f178d6b73e  9E2Ci7r7
b96228d54ad202fa43217b4c2954c8540591505ec3f126305bfc3e785bf45a27  Ds4StPpk
88bc411202ab8c7d4ebc10fac9268101730c9124681673b9988586876bea651e  IihMQr2S
7cb005d4842b180bfa8c4daef705dff83c7138895425bab63d67a546e4dd1a9f  NULNnaKd
c914f8e7f55fe0dae00df7de2f563b94a35bca3d9681007a6bfd4aa5629b3841  RH4yp5nD
79f5d012bffbb470bc99eaf9611eb5ce8c7bd16db0860ede7b13061c67bc1ee9  WjjIvWrX
0a76cda0ad8b2f8708849ea745dc3ffd183f166045d71cb13b077863ed6424fc  aCxWJytK
adf13189231f1b754b55284fb88ba95ca6ce8b3c35243455f480b26775da5a3f  ePMDz1YQ
45afcd76457a40c97f9659a05cd13d0337b0889f42a0ae4070df28d9a1ac153b  jGGKUWQ9
a5850db06498c64254d80704ece0d78b2ff48c40654d87d2b51b5214fbff8aef  oNq64S7j
7a5937e19c0a1cc4700c75e4cf61bb9750192dfa3a21f87a5efd7144aa560622  t3cJ6Gfp
9111a115589f859c5a6e40b4eb933b09413f03ef3b942826455704ede7929af1  x0ODxbKK
884ddbd229e1d6c068a52593d16482d095d13382bde76ee0d2c48297dcd823cb  2SLddvKm
309f7a2437d77f542d742b4c8433b9760ece3a28e0b06376df6367ddf93055bc  5aE4Zjfg
6398aa8391d0428b8e79ad4e8a1405bb270ac470ebed89c8f265eb0451181307  9LgFu97C
fb5a9c8fd90a25c6ba235fe9a628b20d13ce83e4334d03aef3d8493f0b966a9d  DxLqi3sV
c67d10e1a117c9e19bf6ab0396f9f079440ab9da4472387705afd3dbe94c69b4  Ijh6n9yp
668d9e5e57046173395fb63acdfaa81ff1bf3b95c28ca33e5c775a25ca639e7a  NbwekSHV
076208aac8a77aac84099cb194332245b28833d90572a194a34235546daec8b8  RHX0dhSU
143885cf956a038b2431e6a26467cdd1edba02262e34dae76b4f6c8cb15c2841  WpLyF4xC
c5d0c0c77f7f587dbe4ff6815e1a9118adcbe883eedd26d211fc2fb4a8490000  aR087rW1
e8ef074570d9f9216d3b4307ad34a6318bfa7e09bdb99690a94e31c86e55842d  eqMPkSW0
46d9aec14ab002ed547afd904c0ee870e89e80d0b75c5fde80a12975f86c3bae  jQrw8bQO
2c15b651913537f4216378ff7c4a1918801106afb9c5b21dc165935b3866bb0e  oX1HkX8C
87b3755499a7f9ec32b58f824497e0430b56caf1fc9a5277e040931d295bbe44  tYVdC1Z0
c3c23fd9f25161a0035e5da701217a503c07c2e319d4ad142582b7f2282c2d35  x0THPKVQ
95378cce58d7294397ea548531b741c930541ec263b1bd493b1a614d2bc5aca5  2y6eiPnY
42973faba65fb71a21f0be92df8ce8e1a125d4cb63040ff6f3c2940a33c91391  5guDO1cS
dfd1c4c8ebb2a7182215628189d6d9e2f94442851587c67449bbbb35e59a6fe2  9hbn5BeA
403f37e76707172160f04ed6a9504577ae21a64566c6726513f34d50f822e691  DyULYdws
c353941de39d0f499f8209894b87271c686f9ed24777d6e9b8597e2fcecca2c7  Iqbw9pQz
8e162fd2690eec9cf078f73e3d5b69dd5cadacc1445cda4200c58954ef50657d  O5vpRSXk
95637288a9ab3da1ce9b8cfa0d94113130fc3a9aa6b4ad98997f564bc1d86850  S7zBjDOu
18ebedda8b2cb23c4654e46952279b1baa55044bcef4826605856c060d77ce89  WruPiHQS
4fd79cb8de09d7442630f056b2f53c96eb69697979e5c1da0b634c5fc56e4ae2  b9BDTW02
90df23c896109b9efe024c5db6a6e0d86baea53ac94c9b0dedbfbafa38b8249d  eyrV73UR
a0733685ed7b4ac960c93b436bfe0ed8d7951bc4e7c36e88bce9e11c440ff88e  jS1LPICH
007a2a95c38ecbc60d4397ea23e78d80f66df0fdc1ab6da3bc40b946a220ec72  opYpNJ2C
37519abebb056c68fd80d906dd14156640b71699b908c76bdabb711daf646230  tqcK3Nrs
d412711f9b1b3a52603441c833d6624e27f51a9b80e6cfc6379ab257dfb9a08d  xPX9SADx
c422793ffec6bb8b5602ec5a7ae05abd8761fd9479903ab863379607920ed104  2ypuxhr6
507bd8c2cf6263f43e12316ba1540541f4457a061c667397a24ab47447e6851e  5oxXh5Er
e0d7b24c4d84891c1fc8f3968911e5932e80b55d709b221d480bd176ac7fbd98  9twFwHiq
4e6d2443841f31671acbb9e5b7c35a0c02a5075b9b325d79179b7e2b6b79c2e3  EI5Rua6h
a4728e5d090507ee411759bbcf3073d7a305be0a4d856d1c07428b48bba06a9f  JHLXVG98
454a72f9354c59571244685ba6835d3f752b58f7cc4372278107e88b39225da9  O8mpr58x
6cec547c3b92dd27fb74c0c27bd61e2c170923cf0c01a41a5cee8c473a11db62  SOpZbONn
52c9b94fc51de375d02bba6897354a7e97bd7573cb2e022067ce807ee42d214c  XKypMMiJ
ba7daabeff21c6465e8214b039ed49821bd8b4bf28aee5f107a98f0ddec7174c  bJ8uPssG
f23046a5e9f1964a9bb81d017bad80b827aab48527c3e7c7a0ad1bb3b6994177  fANUtdte
c3aa5b21307d698126130bcef215ac9829a506ab7f9b1361da1e8c245eb005c4  jg2ztGlp
289248d1bb64efec318ef40fb10633a65c10af562bd2d25c84220051a15af050  p0yUpsYe
ce222b6b65e012e7a0209bc9951690597779b042d556a6f2015b1c21b9901a09  uF2fheP1
dd7df9683d05b5eed8c280eedbafd2c2fa01868c649eb94cc79d753e0e254499  xa0pHpo3
585f5acca06e7c1d47cc3871654206fa70adeecc39cd8c584f77d52f8a4d3419  34asQJAj
ddcfd164213fa595f38b103d0436c39ce383bad8303e0609d5d328356c7cde7a  5uH65mOX
fb47580434abe1c8177cd757f32d08d74c3445776c8f487db0a987828026b92c  AHwWjpbL
4c29d7fe7d4c1498418c49bb9c20df5eae2b6067f65b2eebf7ffea74eb81572b  EtkxnTjE
74d7f30eb65b30657c517e1b4d70cf6e4d47103c9da773aa539bda1ea712a956  JKlfmBiL
a8a95903fa5337abcac799769cee16ec354661351f89f7ad9b1dbb81a49dd032  OFSlnCKK
2880efaf431ff729cf2b7f8cc3d3e8934893dd336996081eea36a2260d424cc6  SXfbixMa
750b63262b65068258396891e77f7afa851394bde7a9c8c3098cbf8ae1ddb5e5  XZocCx02
77fd76cc340322ae8a41d8f87d5951b0c60949bf7a1d51d901e90f27e5141b83  bJquvh3E
5c9d5df75a524bdb064fc6c49d7d9abde624b1994dfc896a3a54e4d9e8ab1076  fFbQAlD7
70086a1d65272fcd55e417986c4684f9f86943de88ad93f5b7c6d69ca825a500  jpTG7wle
dcc077e5d75839805b8cf90bcd85e0213e2a418d551f2229a99c75365397b32c  p8McbjLN
6b22bc5d41ab8d43ee09c94756001d16aef5f9b04e51108543e35b80c79b1690  uFoxxMAD
b2446a99ef12511def4327e9504d527cc7de79dc4eb84bab5b6397a5e8c10513  y2TwAQsl
bbce48808c1a06ba47e9434e289b3b3e7e7cc8219d6853417c4bf135b42458d1  3FS3M7tr
cc3c691e0a2a275d32a8053c12224af4e3fb999db15a72f1cc5325098a07deb8  6GarVCiO
5e44db07e934c2dd969458e30315968206b045c1fdc3547d34b35263f229bbb3  ANd9SGuS
a0284a0b9ded5bccbf028caaf2fe3dde70cb48592235b7ded9abd95f11e3a48a  EwczAgxU
5e283b6d019cccf1dce1e6e2e7019d02337f8835f430dfa8b7c48905f32af0cc  JPzzPv2R
d69c85eab19d904cd5b87221c1ba1603a5ea3e17fbc76cb1b7e6ad31b7c438fe  OHWOluJj
eb5d4024a654c9118dec859745745a864f544737dc359535b69928b35c6555ac  SibjLvWM
2a5f932d98aac9a4ed47b34c52225286b793e5aaf4d722448e4bcdae5d07fe72  Xkrt40pJ
2fd9ca2343a1cb251e1cf91a173be3b49ed959f4f29a84b9afe9bf8726c9a4c0  bOxuzUXf
f73af464819c557059ab54ff29f6829dd8192668135cb7a669ce151d64cc60b5  fG3pxqYw
55813904319e7c9140ff0a35e5dbf99ea63b4613a95c02adf1108bef200a25e8  k1uy8MT2
43b0bb9e34a853f07dc21a7a3ffb954c249acbe7ea5649bd773ef2c7b9051e7d  pGy7EVYy
4eaf000af731b44485e16646f9ae132778d1bc99997a6104fddf44af765d6bf1  uHK0HPxg
00ae7e498b319b92bc56ae2562fa2c8535062260c77c3cf66f9fa0d6ae3c662e  yCXEcn1e
```
:::
用notepad/vscode/任何文本編輯器 按下`ctrl+f`查詢題目所給的校驗碼
![image](https://hackmd.io/_uploads/ByNRYmNXZx.png)
會是`87590c24`這個檔案
`cd ..`回到上層資料夾
然後執行 `./decrypt.sh files/87590c24`
![image](https://hackmd.io/_uploads/SJY_YQNXbg.png)
```
picoCTF{trust_but_verify_87590c24}
```
![image](https://hackmd.io/_uploads/S1F9FX4mWl.png)

## Day 14  2025/12/23-picoCTF strings it
![image](https://hackmd.io/_uploads/Hkcwce_QZg.png)
首先打開`strings`
![image](https://hackmd.io/_uploads/B1l0qg_7Wx.png)
`ctrl+f`搜尋`picoCTF`
![image](https://hackmd.io/_uploads/ryHWjgd7Zl.png)
```
picoCTF{5tRIng5_1T_FB7D7Bb6}
```
![image](https://hackmd.io/_uploads/HyqGiluXWl.png)
## Day 15 2025/12/24-picoCTF fixme2.py
![image](https://hackmd.io/_uploads/SJ-cYLFmZl.png)
`fixme2.py`:
```python

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x58) + chr(0x18) + chr(0x11) + chr(0x41) + chr(0x09) + chr(0x5f) + chr(0x1f) + chr(0x10) + chr(0x3b) + chr(0x1b) + chr(0x55) + chr(0x1a) + chr(0x34) + chr(0x5d) + chr(0x51) + chr(0x40) + chr(0x54) + chr(0x09) + chr(0x05) + chr(0x04) + chr(0x57) + chr(0x1b) + chr(0x11) + chr(0x31) + chr(0x0e) + chr(0x51) + chr(0x5c) + chr(0x44) + chr(0x51) + chr(0x0a) + chr(0x5b) + chr(0x5a) + chr(0x19)

  
flag = str_xor(flag_enc, 'enkidu')

# Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)
```
打開之後vscode就先報了錯
![image](https://hackmd.io/_uploads/rJZjt8YXZe.png)
運行之後的報錯提示
![image](https://hackmd.io/_uploads/HJGB98tmZl.png)
結果是少一個=所造成的問題
我們把它加上
![image](https://hackmd.io/_uploads/rynwqUFmbe.png)
耶
![image](https://hackmd.io/_uploads/H1FO9IFmWx.png)
```
picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
```
![image](https://hackmd.io/_uploads/HkTt5UYX-l.png)

### 啊?為什麼
在程式語言裡，=是用來指定給變數一個值的
像是
```python
a=100
```
而這個程式碼是要判斷flag是不是""
而判斷會使用==
```python
if flag == "":
```
所以把原本是指定意義的=再加上去一個就可以正常判斷了!
基本上所有程式都是這樣判斷的
## Day 16  2025/12/25-picoCTF Unminify
btw聖誕節快樂
![image](https://hackmd.io/_uploads/Bypj9o5X-g.png)
網站打開來長這樣
![image](https://hackmd.io/_uploads/Hyzp9jcQZg.png)
右鍵-檢視網頁原始碼
![image](https://hackmd.io/_uploads/S1RR5iqXWx.png)
然後`CTRL+F`搜尋`picoCTF`
會在第十五項看到Flag
![image](https://hackmd.io/_uploads/BkGmsjcQZl.png)
```
picoCTF{pr3tty_c0d3_622b2c88}
```
![image](https://hackmd.io/_uploads/HkuNsjqXbx.png)
## Day 17  2025/12/26-picoCTF First Find
![image](https://hackmd.io/_uploads/HJge5gn7We.png)
`files.zip`:![image](https://hackmd.io/_uploads/r1bz9g3Xbg.png)
![image](https://hackmd.io/_uploads/BJWH9gnQbe.png)
直接搜尋`uber-secret.txt`
![image](https://hackmd.io/_uploads/H138ce2m-e.png)
```
picoCTF{f1nd_15_f457_ab443fd1}
```
![image](https://hackmd.io/_uploads/BJX_qln7Wx.png)
> 這麼簡單還要出??

## Day 18  2025/12/27-picoCTF Includes
![image](https://hackmd.io/_uploads/rkHe6E6mWl.png)
會到這個網頁
![image](https://hackmd.io/_uploads/H1bmpEpQbx.png)
右鍵-檢查-原始碼
![image](https://hackmd.io/_uploads/S1ok0EaQ-g.png)
`script.js`和`style.css`就能發現flag的頭和尾
![image](https://hackmd.io/_uploads/SJeBC4pQWe.png)
![image](https://hackmd.io/_uploads/HJaHA4aQ-l.png)
並起來
```
picoCTF{1nclu51v17y_1of2_f7w_2of2_b8f4b022}
```

![image](https://hackmd.io/_uploads/ByYjxS6XZx.png)


## Day 19  2025/12/28-picoCTF HashingJobApp
![image](https://hackmd.io/_uploads/ByfnOt0XZg.png)
先連線到他給的伺服器`nc xxx.picoctf.net (port)`
![image](https://hackmd.io/_uploads/HJQlKt07Zl.png)
然後使用[站長工具](https://tool.chinaz.com/tools/md5.aspx)來加密
結果要看32位[小]
![image](https://hackmd.io/_uploads/H1xIYKRmWe.png)
然後像我一樣把所有的題目加密完
![image](https://hackmd.io/_uploads/rJ5wYtR7be.png)
就會有flag了
![image](https://hackmd.io/_uploads/Syi7iYRQ-e.png)
```
picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}
```
![image](https://hackmd.io/_uploads/r1XFYtCm-l.png)

## Day 20  2025/12/29-picoCTF Collaborative Development
![image](https://hackmd.io/_uploads/HyuYepJNWx.png)
先給電腦裝一下[git](https://git-scm.com/install/windows)
![image](https://hackmd.io/_uploads/B1hQ-61V-x.png)
![image](https://hackmd.io/_uploads/SJQHZ61V-l.png)
讓git添加到系統pach
一路next
然後等它裝完後在檔案的下面跑cmd
![image](https://hackmd.io/_uploads/SkEqZa1Vbg.png)
`git branch -a `
![image](https://hackmd.io/_uploads/SkxnWakNWe.png)
然後使用 `git diff feature/part-1..feature/part-2 && git diff feature/part-2..feature/part-3`
這裡參考了[這篇文章](https://medium.com/@vgqxjb/collaborative-development-9c1875e7dce2)
![image](https://hackmd.io/_uploads/rkSUMayN-g.png)
![image](https://hackmd.io/_uploads/r15Ifp1EZe.png)
```
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ae8dd33}
```
 ![image](https://hackmd.io/_uploads/B151QayNZx.png)
> 文章要換地方了 hackmd->zackzheng's blog
## Day 21  2025/12/30-picoCTF PW Crack 1
<img width="950" height="746" alt="image" src="https://github.com/user-attachments/assets/6f802ac3-9e5b-4025-b004-3fe79a95d070" />
先用vscode打開資料夾
<img width="321" height="200" alt="image" src="https://github.com/user-attachments/assets/5a516e9a-a435-454f-bb67-f3a4873b11c4" />
然後執行 `level1.py`
<img width="1117" height="93" alt="image" src="https://github.com/user-attachments/assets/b16129f6-6403-4e51-acca-2d2e12d2fb80" />
密碼是8713
<img width="1005" height="123" alt="image" src="https://github.com/user-attachments/assets/4cf8703f-77da-460f-94af-e08689061bb6" />

```
picoCTF{545h_r1ng1ng_1b2fd683}
```

<img width="619" height="108" alt="image" src="https://github.com/user-attachments/assets/af11e4c5-864a-4c8d-9f54-59943c60e2b0" />
### picoCTF WebDecode
<img width="960" height="710" alt="image" src="https://github.com/user-attachments/assets/04d99dfd-2f0e-4ff4-8d7b-a9bc84458467" />
<img width="1915" height="947" alt="image" src="https://github.com/user-attachments/assets/41695d15-bbbd-46b3-a6f7-01abb92de160" />
右鍵-檢查
你應該會在 `about` 看到怪怪的東西
<img width="1897" height="936" alt="image" src="https://github.com/user-attachments/assets/2a8b3fa5-68cd-4509-9a54-a2acbeb5a1cc" />

**這絕對是base64**

<img width="1027" height="766" alt="image" src="https://github.com/user-attachments/assets/a55efff4-8098-4039-9d53-12d5c56279a6" />

```
picoCTF{web_succ3ssfully_d3c0ded_10f9376f}
```

<img width="128" height="59" alt="image" src="https://github.com/user-attachments/assets/7242233a-1507-4039-a0e9-6594db197541" />

## Day 22  2025/12/31-picoCTF
## Day 23  2026/1/1-picoCTF
## Day 24  2026/1/2-picoCTF
