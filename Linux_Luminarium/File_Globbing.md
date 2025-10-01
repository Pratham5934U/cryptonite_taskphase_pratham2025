# File Globbing

## 1.Matching with *

**Flag:**   
pwn.college{kyhqfBOX6N1ydbOK2N3jyTNX8Q2.dFjM4QDLzcTN0czW}

**Procedure:**    
First I used 'cd' command and passed '/ch*' to change the directory and then use '/challenge/run'. 

**Code:**    
```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kyhqfBOX6N1ydbOK2N3jyTNX8Q2.dFjM4QDLzcTN0czW}
```

## 2. Matching with ?

**Flag:**     
pwn.college{gcLJPHOavuhaHbYaE9QZNuC0Q_W.dJjM4QDLzcTN0czW}

**Procedure:**   
Here I had to use '?' inplace of 'c' and 'h' and use 'cd' command first then '/challenge/run'

**Code:**
```bash    
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gcLJPHOavuhaHbYaE9QZNuC0Q_W.dJjM4QDLzcTN0czW}
```

## 3. Matching with []

**Flag:**    
pwn.college{s1VbfUOCX5wFEGupzrI2EDv8u1L.dNjM4QDLzcTN0czW}

**Procedure:**             
In this challenge I had toh change directory to '/challenge/files' then run '/challenge/run [bash]' so the characters b, a, s and h get matched which were in the name of files file_b, 
file_a, file_s, and file_h

**Code:**     
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{s1VbfUOCX5wFEGupzrI2EDv8u1L.dNjM4QDLzcTN0czW}
```

## 4. Matching Paths with []

**Flag:**       
pwn.college{opcPK_SXh70BpcaMiGbGQb-Aci0.dRjM4QDLzcTN0czW}

**Procedure:**        
Here I had to run a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files

**Code:**         
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{opcPK_SXh70BpcaMiGbGQb-Aci0.dRjM4QDLzcTN0czW}
```

## 5. Multiple globs

**Flag:**
pwn.college{MToZHH9YKJ0HV0Oe6XuQQRiEjF4.QXycTO2EDLzcTN0czW}

**Procedure:**
Here it was clear from the challenge that i had to just `cd` to `/challenge/files` and then run `/challenge/run` and pass the agrument that it executes every file which has p in it so i did that by passing `*p*`.

**Code:**
```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{MToZHH9YKJ0HV0Oe6XuQQRiEjF4.QXycTO2EDLzcTN0czW}
```

## 6. Mixing Globs

**Flag:**     
pwn.college{k_9rOqHkA2OG-wp_puzbx6RHxij.dVjM4QDLzcTN0czW}

**Procedure:**       
In this challenge after changing the directory I first tried to get the files using [n] but the expansion was not successful, I also tried using [in] but again failed after that I 
tried [pec]* and I got the flag, what this argument did was that it match the files with the first character p, e or c.

**Code:**       
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [n]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[n]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [in]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[in]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [pec]*
You got it! Here is your flag!
pwn.college{k_9rOqHkA2OG-wp_puzbx6RHxij.dVjM4QDLzcTN0czW}
```

## 7. Exclusionary globbing

**Flag:**     
pwn.college{8mxZWJycwfo5josfYqi_TrRcLv1.dZjM4QDLzcTN0czW}

**Procedure:**      
Here I had to just do not match the files which start with character p, w and n using [^pwn]* .

**Code:**       
```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{8mxZWJycwfo5josfYqi_TrRcLv1.dZjM4QDLzcTN0czW}
```

## 8. Tab completion

**Flag:**
pwn.college{gPZHSeNVBvz2xEMygjn75KnR5W3.QX0QTM3EDLzcTN0czW}

**Procedure:** 
Here the trickery was that if i fully type the the whole command then i won't get the flag like in the wriiten code the second attempt so i had to write till `cat /challenge/pwn` then press tab so it got completed automatically after doing this and running it, I got the flag.
`Intrestingly if I use up arrow key then also i get the flag`

**Code:** 
```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{gPZHSeNVBvz2xEMygjn75KnR5W3.QX0QTM3EDLzcTN0czW}
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
```

## 9. Multiple options for tab completion

**Flag:**
pwn.college{gadaQyDu9GwGqXI5obj7aXOlySF.QX2QTM3EDLzcTN0czW}

**Procedure:** 
Here also it was clear from the challenge that I had to use `TAB` to complete the names of files stored in `/challenge/files` and find out in which file the flag was stored. 

**Code:** 
```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn-
pwn-college     pwn-the-planet  
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn-college
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn-
pwn-college     pwn-the-planet  
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn-the-planet 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-
cat: pwncollege-: No such file or directory
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-family 
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{gadaQyDu9GwGqXI5obj7aXOlySF.QX2QTM3EDLzcTN0czW}
```

## 10. Tab completion on commands

**Flag:**
pwn.college{we7K5Z-bCjWi-rmw_zMw-BF7Agc.QX1QTM3EDLzcTN0czW}

**Procedure:** 
It was clearly given in the challenge that I had to just type `pwncollege` and click on `TAB` to auto-complete the command that will give me the flag.

**Code:** 
```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-28422 
Correct! Here is your flag:
pwn.college{we7K5Z-bCjWi-rmw_zMw-BF7Agc.QX1QTM3EDLzcTN0czW}
```