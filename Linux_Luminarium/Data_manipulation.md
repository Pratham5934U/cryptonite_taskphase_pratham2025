# 1. Translating charactors 

**Flag:**
pwn.college{QGFI-767Ppya1hvb2TxYOPTkt2u.QXzETM3EDLzcTN0czW}

**Procedure:** 
It was clear from the challenge that i had to use `tr` in order to translate every charater to swap their casing.

**Code:**
```bash
hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz
your case-swapped flag:
pwn.college{qgfi-767ppya1hvb2txyoptkt2u.qxzetm3edlzctn0czw}

hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{QGFI-767Ppya1hvb2TxYOPTkt2u.QXzETM3EDLzcTN0czW}
```

# 2 Deleting characters

**Flag:**
pwn.college{42BUNfaNqcNt-xfnGINZqn6f82v.QX0ETM3EDLzcTN0czW}

**Procedure:**
Had to just delete "^" and "%" in the flag using `tr -d`.

**Code:**
```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{42BUNfaNqcNt-xfnGINZqn6f82v.QX0ETM3EDLzcTN0czW}
```

# 3 Deleting newlines

**Flag:**
pwn.college{EKB4aVNiR7xJw4s6TVfUGTnAArM.QX1ETM3EDLzcTN0czW}

**Procedure:**
Here i had to delete new lines using `tr -d "\n" to get the correct flag. 

**Code:**
```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{EKB4aVNiR7xJw4s6TVfUGTnAArM.QX1ETM3EDLzcTN0czW}
```

# 4 Extracting the first lines with head

**Flag:**
pwn.college{4HOAHKSv9XuT-bm-Hyz8SDnbyNg.QX2ETM3EDLzcTN0czW}

**Procedure:**
Clearly stated in the challenge that I had to pipe the out of first seven lines of `/challenge/pwn` to `/challenge/college` to get the flag.

**Code:**
```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{4HOAHKSv9XuT-bm-Hyz8SDnbyNg.QX2ETM3EDLzcTN0czW}
```

# 5. Extracting specific section of text

**Flag:**
pwn.college{UYENQcHblG6GzLeub_f2s24Cdfe.QX3ETM3EDLzcTN0czW}

**Procedure:**
First I printed out the ouput of `/challenge/run" to observe the format which has to be filtered out then used the follwong conditions as in the code to filter out the flag.

**Code:**
```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
32101 p
8616 w
12068 n
2676 .
26040 c
9171 o
7467 l
614 l
8532 e
20864 g
10987 e
16900 {
16125 U
24575 Y
26521 E
265 N
7400 Q
30286 c
1264 H
10620 b
10790 l
18607 G
433 6
12176 G
11588 z
31423 L
20064 e
1538 u
9604 b
15302 _
22961 f
10895 2
7195 s
22887 2
8774 4
19261 C
20604 d
403 f
24456 e
38 .
16767 Q
1475 X
23468 3
11240 E
18000 T
26136 M
18625 3
30754 E
5563 D
24666 L
29747 z
29298 c
19870 T
23794 N
21362 0
6248 c
2166 z
4089 W
14412 }
hacker@data~extracting-specific-sections-of-text:~$ /challlenge/run | cut -d " " -f 2 | tr -d "\n"
bash: /challlenge/run: No such file or directory
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{UYENQcHblG6GzLeub_f2s24Cdfe.QX3ETM3EDLzcTN0czW}
```

# 6. Sorting data

**Flag:**
pwn.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXwQzM4EDLzcTN0czW}

**Procedure:**
Here I used `-r` with `sort` command so that the correct flag appears on the top of all decoy flags.

**Code:**
```bash
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXwQzM4EDLzcTN0czW}
pwn.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXwQzM4EDLzcTN0bzW}
pwn.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXwQzM4EDKzcTN0czW}
pwn.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXvQyM4EDLycTN0czV}
pwn.college{wq8Imq_hg3GMVLNekXJln-0o76V.QXwPzM4ECLzcTN0czW}
pwn.college{wq8Imq_hg3GMVLNdlXJmn-0o76V.QXwQzM4EDLzbTN0czW}
pwn.college{wq8Imq_hg3GMVKNelXJln-0o76V.QXwQzM3EDLzbSM0bzW}
pwn.college{wq8Imq_hg3GLVLNelXJmn-0o76V.QXwQzM4EDLzcSN0czW}
pwn.college{wq8Imq_hg2GMVKNelXJmm-0o76V.QXwQzM3EDLycSN0bzW}
pwn.college{wq8Imq_hf3GMVLNelXJmn-0o76V.QXwQzM4EDLzcTN0czW}
pwn.college{wq8Imq_hf3GLVLMdlXJmn-0o76V.QXwQzM4EDKzcTN0czW}
pwn.college{wq8Imq_hf3GLUKNelXJmn-0o76V.QXwQyM4EDKzcSN0czW}
pwn.college{wq8Imq_gg3GMVLNelXJmn-0n76V.QXwQzM4EDLzcTN0czW}
pwn.college{wq8Imq_gf3GLVLNelXJln-0o75V.PXwQzM4EDLzcTN0czW}
pwn.college{wq8Imp_hf3FMVLMekXJmn-0o76U.QXwQzL4EDLzcTM0czW}
pwn.college{wq8Imp_gg3GLVLNekXJmm-0o76V.QXwQzM4EDLzcTN0bzW}
pwn.college{wq8Ilq_hg3GMVKNdlXImn-0o76V.QWvQzL4DDKzcTN0czW}
pwn.college{wp8Imq_hg3GMVLNelXImn-0o76V.QXwQzM4EDLzcTN0czW}
pwn.college{vq8Imq_hg3GMVKNelXJmn-0o66V.QXwQzM4EDKzcTN0czW}
pwn.college{vp7Imq_hg2GMULNdlXJmn-0o76V.QXvQzM3EDLzcTM0czW}
pwn.collegd{wq8Imq_hg3GMVLNelXImn-0o76V.QXwQzM3ECLzcTN0czW}
pwn.collegd{wq8Imq_gg3GMVLMelXJmn-0o75V.QXvQzM3EDLzbTN0czW}
pwn.collegd{wq8Hmq_hg3GMVLNelXIln-0n76V.PWwQzM4EDLzcTN0bzW}
pwn.collefe{wq8Imq_hg3GMVLNelXJmn-0o76V.PWwQzM4ECKzbTN0czW}
pwn.collefe{wq8Imq_hg3GMULNelXJmn-0o75V.QWwQzM4EDLzcTN0czW}
pwn.collefe{wq8Ilq_hg2GMVLNelXJmn-0o76V.QXwQzM4EDLzcTN0czV}
pwn.collefe{wp8Ilq_hg2GMVLNelXJmn-0o75V.QXwQzM3EDLzbTM0czW}
pwn.colldge{wq8Imp_gg2GMVKNekXJmn-0o65V.QXwQzM4DCLzbTN0czW}
pwn.colldfe{wq8Ilp_gf2FMVLNelWJmn-0n66V.QWvQyM4EDKzcTN0byV}
pwn.colkege{wq8Imq_hg3FMVLNelXJmn-0n76V.QXwQzM4EDLycTN0czW}
pwn.colkege{wq8Imp_hg2GMVLNelXJmn-0o66U.QXwPzM4EDLzbTN0czW}
pwn.colkegd{wp8Imq_hg3GMVLNdkWJmn-0o66V.QXwPyM3ECLzcTN0czW}
pwn.colkefe{vq8Imp_hf3GMVKNekXJmn-0o76V.QXwQzM4EDKzcTN0czW}
pwn.colkdfe{wq8Imq_hg2GLULNekXJmn-0o66V.QXvQzM3EDKzbTN0cyW}
pwn.coklege{wq7Ilp_hf2FMVLNelXJlm-0n65V.PWwQzM4EDLycTN0czW}
pwn.coklege{vq7Imq_gg3FMVKNekWJmn-0o66V.QXwQzM3EDKzcSN0czV}
pwn.cokkefe{wq7Ilp_hg3GLUKNelWJln-0n76U.QXvQzL3EDLybTN0byV}
pwn.cnllefe{wq7Imq_hf2FMVKNelWJmm-0o76U.QXvQyL3ECLybSN0czW}
pwn.cnllefe{vp8Hmq_gg3GMVLNekXIln-0o76V.QWwQzM3DDLycTN0cyW}
pwn.cnlldge{vq7Imp_hf3GLVLNekWJmm-0o66U.PXwQzM4DDLycTN0bzW}
pwn.cnlldfe{wq8Hmq_hf3GMULNelXJmn-0o66V.QXwQzM4EDLycSN0cyW}
pwn.cnlldfe{wq7Imq_gg3GMVLNdlXIlm-0o76V.QXwQzM3EDKzcTN0byW}
pwn.cnlkege{wq8Imq_hg3GMVLNelXImn-0o76V.QXwQzM4EDKzcSN0cyW}
pwn.cnlkege{wq8Imq_hf2FMULNdlXImm-0n76U.QXvPzM4EDKzcSM0cyW}
pwn.cnlkdge{wq8Hlq_hg3GMVLNelXImn-0o76V.PXwQyM4ECKzcTM0cyV}
pwn.cnklege{wq8Imp_hf2GLVLNelXImn-0n76V.QXwPyL4EDKycTM0bzW}
pwn.cnkldge{wq8Imp_hf3FLULMdlXJmn-0o66V.QXwQyM3DDKybSN0cyV}
pwn.cnkldfd{vq8Hmq_hg3GMVLNelXJln-0o65V.QXwQzM4DDLycTM0czV}
pwn.cnkkefe{wp8Ilp_hg2FMVLMelWJmn-0o66U.QWwQyM4DCKzcTN0cyW}
pwn.bollegd{wp8Imp_hg2GLULNelWJmn-0n65V.PWwPzL4ECKzcTN0czW}
pwn.bnllege{wq8Imp_hg3GLUKNelXJln-0o76V.QXwQzM4EDLzcTN0cyV}
pwm.college{wq8Imq_hg3GMVLNelXJmm-0o76V.QXwQzM4EDLzcTN0czW}
pwm.college{wq8Imq_hg3GMVKNelXJmn-0o75V.QXwQzM4EDKzcTN0czW}
pwm.college{wp8Imq_hg3GMVLMelXJln-0n76V.QWwQzM4DDLzcTN0czW}
pwm.college{wp8Imq_hf3GMVLNelXJmm-0o76V.QXwQzM4EDLycTN0czW}
pwm.college{vq8Imq_hg3GMVLNelXJmn-0o76U.QXwQzM4EDLzcTN0czV}
pwm.coklegd{vp7Imq_gg2GMULNelXImn-0o76V.QXwQzL4DDLzbSM0czW}
pwm.coklefe{vp7Hlq_gg3GMVKNelWJlm-0o66V.QWwQyM4EDLzbTN0byV}
pwm.coklefd{vp8Imp_gg3GMVKNekXIlm-0n76U.PWwPzL4EDKycSN0czW}
pwm.cokkdge{wp8Hlp_gg3GLVLMdlXImn-0o76U.QWvQyL4ECLybTN0czV}
pwm.cnkkege{wq8Ilq_hf2GMVLNekXJmn-0o76V.QWwQzM4EDKzcSN0cyW}
pwm.cnkkdge{wp8Hlp_gg2GMULMekWImm-0o66V.PXwQyM4EDLzcSM0czW}
pwm.bollegd{vq8Ilq_hg2GMVLNelXJln-0n76U.PXvQzL4DDLycTN0cyW}
pwm.bollefe{wq8Hlq_gg2GMVLNelWJmm-0o76V.PWvQyL4DDLycSM0cyV}
pwm.bolldge{wq8Ilq_hg2FMVLMekWIln-0n76U.QXvPzM4ECLybTN0bzV}
pwm.bolldge{vq8Hmq_hf3GMULNelWJln-0o65U.QWvQzM4EDLzbTN0cyW}
pwm.bolkegd{wp8Imq_hg2FMVLNelXJmn-0n76V.QXvQzM4EDLzcTN0cyW}
pwm.bokkege{wq7Hmq_gf3FMVLNdkXImn-0o66V.QWwQzL4EDLzbTN0czW}
pwm.bnkkegd{wq7Imq_hg2GMVKMelXJlm-0o76V.QXwQzL4EDKzcSM0czV}
pvn.college{vq7Imq_hg3FMVKNelWJln-0o76V.PXwPyM4EDLzcTN0czW}
pvn.colldge{vq8Imp_gg2GLVLMelWJlm-0o76V.QWvQzM3DDLzcTM0cyW}
pvn.colkege{wq8Imp_hf3FMVKMekWJlm-0o66V.QXwPyL4DDKzcTM0czW}
pvn.colkefe{wp8Imq_hg3GMVLNdkWJmn-0o76V.QXwQzL3DDLycTN0czW}
pvn.cokldge{wq8Imq_gf3GLVLNelXJln-0o66V.QXwPzM4DDLycTN0czW}
pvn.cnllege{wq8Imq_hg3GMVLNelWJmn-0o66V.PWwQzM4EDLzcTN0czW}
pvn.cnllege{wp8Ilq_hg3FMVLNelXImn-0n76V.PWwQzM4EDLzcTN0czW}
pvn.cnklefd{wq8Hmq_hf3GMVLNelXJmn-0o75V.PWwQyM4EDLycTM0bzW}
pvn.cnkldge{wq8Imp_gg3GMULNekXJmn-0n75U.QWvPyL4EDKybTN0czW}
pvn.bollegd{vq7Imq_gf2FMVKNdlXJmn-0n75U.QXwPyM3EDLycSN0byW}
pvm.college{wq8Ilq_hg3GMVLNelXJlm-0o65V.QXvQzM4DDLzcSN0czW}
pvm.collefe{wq8Imq_hf2GLVLMekXImn-0o75U.PXwPzL3EDLzcSN0bzW}
pvm.cnlkdge{vp8Imq_hf3FMVLMekWJmn-0o65V.PXwQyM3EDLzcSN0cyV}
pvm.boklefd{vp8Hlp_hf3GMVKNelWJmn-0n65V.QXvPzM4ECLzcTM0czW}
pvm.bnklefe{vq8Hmq_hg2FMVLNdkXJln-0o75V.QWwQzL3EDKzcTN0cyW}
own.college{wq8Imq_hg3GMVLNelXJmn-0o76V.QXwQzM4EDLzcTM0bzW}
own.college{wq8Imq_hg3GMVLNekXJmn-0o76V.QXwQzM4EDLzcTN0czW}
own.college{vq8Imq_hg3GMULNdlXJmn-0o76U.PXvQzM3EDKzbTN0byW}
own.collefd{wp8Hlq_hg3GMVLNekWJmn-0o66V.PXwPzM4EDLzbTN0czW}
own.colldge{wp8Imq_gg3GMULNelWJmn-0o76V.QXvQzM4DDKzcTN0cyW}
own.colkege{vp8Hmq_gg2GMVKNelXImn-0n76U.QXwQzM3DDLzcSM0bzW}
own.colkefe{vq8Hmq_gg3GMVLNelXJln-0o76V.QXwQzM3DDKzcTM0byW}
own.colkdgd{vq7Imq_hg2FLULNelXIlm-0n76U.PWwQzM3EDLybSM0czV}
own.cokldge{wq7Imq_gf3GMVLMelWJmn-0o65U.QXvPzL3DCKzbSN0czW}
own.cokldgd{vq8Imq_hf3GMVLNelXJln-0o66V.QXwQzM3EDLycTN0czW}
own.cnllege{wq7Imq_gg2GMVLNelWJmn-0o75U.QXwQyM4EDLzcTN0czV}
own.cnllegd{wq7Imq_hf3GMULNdlWImn-0n75V.QXwQyM4EDKzbTN0bzW}
own.cnlldge{vq8Ilq_hg3FMVLNelXImn-0o76U.QWwQzM4EDLycTM0czW}
owm.colkdge{vp8Imq_gg3FMVLMekXIln-0n66V.PXwQzM4DDLzbSN0czW}
ovn.colldgd{vq8Ilq_hg3GMVLMdlXImn-0o76V.QXwQzM4ECKzcTN0czV}
ovm.cokkdfe{wq7Imq_hf3GMVLNdlXImn-0n65V.PXwQzM4EDKycSN0czW}
ovm.boklegd{wp8Imp_hg3GMUKNekXJmn-0o75U.QWwQzM4DCKzcSN0bzV}
```