# 1. Listing Processes

**Flag:**    
pwn.college{sAgPepqi2J4fGyJHClq4N4PmGqD.dhzM4QDLzcTN0czW}

**Procedure:**       
In this challenge /challenge/run was renamed to a random filename and I could not ls /challenge and it was already launched so I had to see running process list, figure out the filename, 
and relaunch it directly for the flag so I got the running process list using ps -ef and found the renamed file and ran it to get the flag.

**Code:**    
```bash
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 20:28 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 20:28 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 20:28 ?        00:00:00 /challenge/6065-run-5615
root          72      68  0 20:28 ?        00:00:00 sleep 6h
hacker        81       1  2 20:28 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry.js --au
hacker       102      81 17 20:28 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry
hacker       143     102  9 20:28 ?        00:00:02 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       158     102  1 20:28 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/bootstr
hacker       221     158  0 20:28 pts/1    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workbench/contrib/terminal/browser/media/
hacker       336     221  0 20:29 pts/1    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/6065-run-5615
Yahaha, you found me! Here is your flag:
pwn.college{sAgPepqi2J4fGyJHClq4N4PmGqD.dhzM4QDLzcTN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

# 2. killing process

**Flag:**    
pwn.college{UAK-dW6BJpzzrejFggOeHotj5ev.dJDN4QDLzcTN0czW}

**Procedure:**    
First I found out dont_run processs using 'ps -ef | grep /challenge/dont_run' then to terminate it I used 'kill' .

**Code:**   
```bash
hacker@processes~killing-processes:~$ ps -ef | grep /challenge/dont_run
hacker        73      71  0 21:22 ?        00:00:00 /challenge/dont_run
hacker       384     223  0 21:22 pts/1    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 71
bash: kill: (71) - Operation not permitted
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{UAK-dW6BJpzzrejFggOeHotj5ev.dJDN4QDLzcTN0czW}
```

# 3. Interrrupting Process 

**Flag:**     
pwn.college{sjyBJ9WI2c2gNwUYWBqfPm5Nply.dNDN4QDLzcTN0czW}

**Procedure:**     
In this challenge i had to interrupt the process run using Ctrl+c .

**Code:**       
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{sjyBJ9WI2c2gNwUYWBqfPm5Nply.dNDN4QDLzcTN0czW}
```

# 4. Killing Misbehaving Processes

**Flag:**
pwn.college{o9cPZfR-bTfJTlTU-829DST6wHU.QX0MzM4EDLzcTN0czW}

**Procedure:**
Here in this challege first I had to kill the process name `/challenge/decoy` so that i can run `/challenge/run` which will pipe the fllag into `/tmp/flag_fifo` but since the `decoy` process had already piped decoy flags in it they were still present when I `cat /tmp/flag_fifo` so to get the correct flag I ran `challenge/run` again so that it now again pipes the correct flag and then in the empty pipe the correct flag was piped which I got by cating `flag_fifo`.

**Code:**

**Terminal 1:**
```bash
hacker@processes~killing-misbehaving-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
    137 ?        00:00:00 .init
    138 ?        00:00:00 .init
    139 ?        00:00:00 su
    140 ?        00:00:00 sleep
    141 ?        00:00:00 sleep
    142 ?        00:00:00 decoy
    167 ?        00:00:00 Xvnc
    172 ?        00:00:00 novnc
    182 ?        00:00:00 .websockify-wra
    192 ?        00:00:00 .xfce4-session-
    195 ?        00:00:00 dbus-launch
    196 ?        00:00:00 dbus-daemon
    201 ?        00:00:00 xfconfd
    210 ?        00:00:00 ssh-agent
    212 ?        00:00:00 .xfwm4-wrapped
    217 ?        00:00:00 .xfsettingsd-wr
    223 ?        00:00:00 dconf-service
    226 ?        00:00:00 .xfce4-panel-wr
    231 ?        00:00:00 .thunar-wrapped
    237 ?        00:00:00 .xfdesktop-wrap
    245 ?        00:00:00 wrapper-2.0
    342 ?        00:00:00 .websockify-wra
    346 ?        00:00:00 .xfce4-terminal
    352 pts/0    00:00:00 bash
    366 pts/0    00:00:00 ps
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ 

```

**Terminal 2**
```bash
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{TzErFzyFeN6yIIjIakkOhBqq2xD4.wuckop4BYu9QBSk4a}
pwn.college{pk0-TT6DOmsNmMsi0lX5pMlmU3z9nffFmH6wT9T12Co6ED}
pwn.college{LEqNjkVQ36g-EXt5FN-TJG6i8EN0mQzYjl4dFxhrdpTKDR}
pwn.college{x13q3NiUF6kDK4NtxQPhnzqJbcK6-R-2ZE4N2snC6Y7k.z}
pwn.college{3JWfTWJMpEq9ycfiSMXf7Q0YrWzwivXKro8qYUR0RZl7OS}
pwn.college{PaS7snwQU7E6.xCYE8Q-lzgQf39HDcsbcOzY7DVZcZEJtk}
pwn.college{BmozwU4Alelen742ANCR90oZaGWXjJQU2ayuSPGzwyWVQp}
pwn.college{m5-LnxLckju8MZfDBpvLv.-al9.K3Smv5hwyM8RAOI5TEv}
pwn.college{fmAQsF6bFthN5F-mny5c7vRIyR1P6a972BnwBuIGXTDS9A}
pwn.college{jL5Q6BTknKs2GwwAGP8xZjlLP7VFuXRZjabJ5oE6wGfdFd}
pwn.college{VcFi2Q.8p88oAd.PVwKdWhj5cJvGOZ3ix0Lw72NGArNC25}
pwn.college{hRIr.A8-FFmKgRgPVlSfbV5eUkzZ0.zGXK7XAlG0lxcHB8}
pwn.college{OCF5Af55CS4n4XcVdCyIgT6J3ajt6w1xiTTSwM23on-jEb}
pwn.college{xGFbCZqVLPRx-kMeMzUpcnApwrrywKjBfptWfb3Jc2boYl}
pwn.college{8PkiAmO9KN4CxXw6ILxDffLEd0JpYE5ty9dOtbcU6eMVOU}
pwn.college{Q2rDWKtMET.oaYA0494CtnMneow9zlp9fmL43OZQ9bB1gy}
pwn.college{aZImWx8iUF0IgF3IK0WHSTDMREdcH83UMQ9SRIoHf5FvQS}
pwn.college{EtFFS1L0o1IvhGrxLtvylXqkeNDYZT6zJU7EPF2egdI2lt}
pwn.college{SEcJVgbGSRe7sZaBBZDL.PvKIquOFnOXNd5VDqFnr5P8PX}
pwn.college{Kw0sMF7uSHL4fliFxqZJf6dOIUJK8MZvVNHSb2J94g16nZ}
pwn.college{rN2oJIL5Jm7T94hYRC922Zs0BJO3gYc8eVX3d9JlUDCoo0}
pwn.college{sulBCofn98zof2JE.309iPb51.fPuVOl5I7fiyKPVY0afi}
pwn.college{cCVkhPNV9jcz4VCPoljQAdVomIXhFoGys99hscNUVJDeBT}
pwn.college{BW9UUES3fh9LLPRg3U.okwiC5jsLS7PGI1uafgPcAqTzQG}
pwn.college{mc0oh.qTti9bY1SimG1XEdKSuqO7Q.bAlozt107pst54iZ}
pwn.college{7RvpRiHRoOYK81noFyt.leprCtgcUKxsl8FPFfFejREnBk}
pwn.college{oAFizLzM0eQcGi7R9ELHTa779uTcRYvDqIP6OAXMwWM.Jr}
pwn.college{l-o.r56x2g3vYNLbbWhcwoaX1MJLPPm8Fk7Q9E7sSu5n3N}
pwn.college{A1QyeK80UJxPYC1jQcV9n1m.Ag84lcDME3JRygW565MH9g}
pwn.college{mWoK64-JPVcHxNs5jYLHR11Rqyfb4tMAcjqPhYBFaT3hCH}
pwn.college{zV5KSQVl5P3qXlZATQYmtezfRMuYlZFpGF.LWFZP00-ul5}
pwn.college{E1HjlmSHAYqnuVEoBSywdGny7SrlYt1e.edgSrotbo52-L}
pwn.college{MsQv4ixgBqnMPM9AX44IiCdjKfrMIOrYpozC0J9xtFBZDg}
pwn.college{UlUyUMXso5sPBmo8rsz12u1e4SqxrHuIypzURSYM1mdhZF}
pwn.college{.aVaIkcekzS9TMSr-CvQRVBA6-BnAoEQXor4550L09vwoE}
pwn.college{eB.1gVmAVmKha9RiZw82W34PqHE9T2sXM4jI289uwnX4Dg}
pwn.college{OslawafSTraxKoXwPuxh6Jo5M2Efw9vEFUQsueIofSA3hu}
pwn.college{DnfjZDn00WVJnmMnQ8P4VDP8K6uAdVSbSZ7LVDFL9R-S04}
pwn.college{kyhgnYnPBvkl1KhafJKxZKQmFU.oKpk6DUd3tieKqEw3Ru}
pwn.college{RJultlu.Ci5501zLGKgkBLCPU7OKVVgzP-t84EGmGtGYhE}
pwn.college{.lfIrUamijwubNIL86To2.piV.dlkGVX2FV-jOFMUiUf2B}
pwn.college{OqCvtU2J2VjWakOfAeoxjFI8qYJp7mvcg7AOSSZnPSo920}
pwn.college{TzWFrWmfAZ7cueLwKruG-e7tE6uvUtsbTKmuwQMGOBhgye}
pwn.college{CyVIWLGcMp9.XbA5bcP9hUevwByjx7dld4JjktXFPtVLqn}
pwn.college{NlI2lRl8GEl77.1rRo7zZhA7jBYlFJWbZCdcbxDw8WQDQE}
pwn.college{hHTuAIc.3TpJJ144q2UtwsuEQYjTI22W-480rqrvnTxWg2}
pwn.college{QEU7lI7vHsWprJMwL6RIxnPzlZ5ohicz-Z-Y9z1ZDKquNy}
pwn.college{Ly.TtkVrEpVjEPqUELf8-cdBDkJSe7K-2bGPDQ9UVhrIG9}
pwn.college{GDgzU4cPjHdsLdbxJgi48MtKUHrjc3-yj4vUkF.Hm7uKjp}
pwn.college{y2j1j9ImObVHug2ACI57F-HZuPfl-gbdjZH.sg8kQ5WW1I}
pwn.college{GVGAO9TyYf1QR-eD82zu7ad3MoaOp1wQH7bktKm2ZexYpU}
pwn.college{j1VH0agOMWZlDy4PxdTW.y5w8U6vOdbDLitUjvZsnLIkwe}
pwn.college{P7uQMAdFEk1JFZFVLyw3Oc3Q3AGKeKypNCSBgYCvciRBa-}
pwn.college{rDLND-jDPIH-UWVFOHman8UZUSZI5XFz.G-RqaJ6Phk9u0}
pwn.college{znxu2o7gBubnq2LcNmCz2souWJrjPJ12UkyKNj0uZgA.vq}
pwn.college{mTR2DCGYviC07nKAvZIKj-l7pMRkHbx2bCwVlAces8XgzA}
pwn.college{y7st6o0AzDpynISTanFcDoE2H9Khb-xItcZwYl2xs2j0rt}
pwn.college{E5TLPfMdKrINg5jP6QUxzzKVO6xd9nFhWTebABZC11Yn3Y}
pwn.college{3WFthUxxheMf-QbGW6vERgk4tY7cgHFAcCD7A-c.qIZH-7}
pwn.college{7S4OR5txpYBPF9qSoyGaEqNAxAihqywikf9GTHpB7m7ltC}
pwn.college{uhrHOSIlwR7CLRpXbDJUDeVQlkHjH9Ob6Uz-Uhm3V7w315}
pwn.college{EDYNa4todimbym5aLRFeO7KULWrcInnvfoRBWlXqbnXpxS}
pwn.college{JwuFxlkDCWXgmAHomd.9I8lrmSDmv7CObpP6AWr0U.ezoK}
pwn.college{dKnIJ2A7vEDhUk2SVGPPYlRvXeA3stuvBzmhV7TEy8qP7g}
pwn.college{fzsHp5HUUZXs9X.fZQpo6X.uZnLZMNa3jkXPxqjXc4rZxI}
pwn.college{Z1Jq3KJmA2AJbLW6ffU3R3WUBMO27FYhx0m.wnxONJiA.e}
pwn.college{HNyKSgis8pPnAs0x80V8P.eFtMagp9notbJxn.g.-tlyYn}
pwn.college{WherAvtU2QQ-PKkP0RZEdTsCDSAeEwcXYvKVM0a72MUa6T}
pwn.college{MZXxKHj8N6ELLHLYZDwpJ2BMVCn-w6C01nXc.DClV-x8bb}
pwn.college{qIe4nvpUTR-GwF1NbPC.zr5FFYKlnQ.HghIgy-RIpg35nQ}
pwn.college{J.eNfZzvPj9WGb0F8SFx58KsdNFW3B2IYJoPN9Z7hyD52t}
pwn.college{3-1N.Ms8hFL6VpIQczSnjjn.XdPH80.aWYvh3tErmmIdyQ}
pwn.college{PFcYJicbs3nQt37UGcf4Ia3jFPAGoSUlp2d5xXqOHQ3UQS}
pwn.college{tYc8GsHcs7J-S6bJa4dYP2bDJR5qI5i5GbyyVOG2Y0XWqi}
pwn.college{LUweghoJuRCGrYTfoXIL-jWjl15H7iE3foDQgv9k4ciCix}
pwn.college{qQtVO4Cp.FJdxoJfPiu2nIkWXADtNUGvRGJEALsR-RLNyA}
pwn.college{8vZTFhAq.Lb3OKTMY5cyDEu7lUAfUuD0hZp5OCHvyuBwkT}
pwn.college{J36wlR5TOeswTW.hvZnAnwS3E4Virj-6LaVeWtFJWn7wet}
pwn.college{P169spjkXwNeHK1XUENxuYow37VKC-gSpYyixf3kdoONqJ}
pwn.college{kEImMjhOiPvl9DFkRRxcl7PjB2CnArvuu9oAZimGaD0bkF}
pwn.college{AKJfMRIj8U2LkgAno0eCaJAk8F01z4eXIN4jeeaJRD2WVg}
pwn.college{imEUIx2k2KpGo3vGrEM2sge19NXdjP249Quu7.1mpGK0C7}
pwn.college{2X7OiYpvs2uw7sd0MpUxCtzsSL9zRkBOFml5pKgYS7nmgl}
pwn.college{no8qcHlEmRTByRhSm4msH-lvK0kmH-SvZTcyyjp2IlYIOl}
pwn.college{0vLedW6RECAzoLRxtzPsQiUWrMizJYjfx4rafev1w8WHI0}
pwn.college{3ZiMLEiN5Kic7nA-8iGlkzGfCeuyKoaBMPVBeYyQNHtRwj}
pwn.college{6SgUEqbuCr4VNYvFJ9FvW.IHNZFuvcwA-5MqTg1QEd-vnr}
pwn.college{tOwo54ZJy.gHPwCb8XCz.wXmR.HtQnKJcFuuX4DxDrF2N2}
pwn.college{NXmISp6d-c5X7-Adu2x.Otp.YnGuu.AclMPxqG1XTSc9UB}
pwn.college{igGgG42cmocFl5ger125Mh27CIbF1A-N8m19HJOencX-78}
pwn.college{q0jfZkQvd9Aw05m0QHjHtIY81RCQ8gKGWUv3y0m-9VOyaW}
pwn.college{rWOW-FCa6.NzF0q3zTa-EtnFPN-jXDIy4zrRMiEvGgxLDQ}
pwn.college{18OxL7LA8Qyjb96BftPySfPv6KEnzcqHNDE6Qj8jav14oS}
pwn.college{xMKU.9iU78dVWyzpSNFmTdz54xJkwmh3mAP09bNnljpHrl}
pwn.college{vGsu60LJlpI4ToE6qrpOILAnVOA9y4B85Q-PGAV7xGkHr6}
pwn.college{5QKboEkTrm.vHsimjiQh7fWv0CTKaB-q4iyTBq3JmFLEHE}
pwn.college{PNtuF0tdMVUdjxMZ.oKoxez6z3XAKi0ltEztvWVibLj1Me}
pwn.college{MOKzMgjq1em1qfEFTTj7Vjuhd4CBm1bFAaIdoLOI48o-oi}
pwn.college{hJGdteUZuHAxrAkCnjK7LUYQ8Uy1nMbFgxDdMJkBg-qKtB}
pwn.college{W9i7Tw4h1dwGwrSmmWuvF5DRmHgGGuRIUoxaMCv1ScNG9P}
pwn.college{ZMN4-Jp92RTWO..8VKZpalNf3uexuazWX2uvOTPcp1z9Q7}
pwn.college{TOE2sBWi74og.J0zpAKvXh6D.o1XNx2Yby8sjkK1Y4CUyv}
pwn.college{L66XICeciKeFcjLvneRtvBOZ3KZeeucPWp.QgH8KKFaZCZ}
pwn.college{CuRqoi7QzJZfIh8kCXcZ0XFEiS7CxyLCoT6PZZH7m9E39-}
pwn.college{n8HYm0XDvzxaebj-fs4YCdFOpDsm4oPvvbXcOChrd8w2Dc}
pwn.college{3yaTy5tSnqBctbCCQyfeR6zx3-3C01iK9J.je7VmF09Unj}
pwn.college{u8aJZEqH1xiHSttEBwpJby.dPajTDTnN1bYomp9pFswuhe}
pwn.college{Phq2D2exMUcNgGNDM8gGjErl5TrTHByRan9iiJe8rgSWVS}
pwn.college{NoIO-tc9nEMiyWDRns2ji3N78EY.IWm21QAlvlMpkveDdj}
pwn.college{72iujBxuRpUji.A58u.EjQasxnY6cUvg-8XPSfUSBZVWEp}
pwn.college{Hlal.GE9b6Jx02fElcGWxp5mu2iht6N9tmI52RXYQEq8tK}
pwn.college{FrqdysBMQdq1NZw33bkmszugPEHkEY1xN60mvfY3z9zGHT}
pwn.college{tnCTx06DLzyt-1k8Yr2WRf2Gig4cl.3vBVaTDsi82d0ANt}
pwn.college{3sx6HUhDRD-gT3Nn6Xm3J-xxPhzBxAsCep7hpjFg.r9IPN}
pwn.college{-vE7DPN7DdBQFaepvMpPHCM25EtFpekB18yKWhvxrQLE7j}
pwn.college{jH1WxtNqw5FmNUn0vjqEn9Tx0o0irH9kKg9E2pN3PhuiNF}
pwn.college{tMzapGpo6UOyodXvOCp1x1WnRubZRM0SE1vDEFkFWRa332}
pwn.college{THPOiBkYPqaW6xOoC1Z.F1JIAIkcOI8R3z-839McweURIb}
pwn.college{RNVm1mYYbbFGsVWwIoEf6IujRnbgM4deUbVuGmyZtPriid}
pwn.college{RGun7SWez1jGCrEb3Y7aX6mNRs1e6t4VBMaRvbNCCk9lTG}
pwn.college{jitgGW.EjdBd5iY6ir9zS02SHqFpev1PLz85Fm7Dtx1dnt}
pwn.college{t7PudUZPeT5S7Yot89wJEBmYcZdfjHqmq93gdNSnB-L7Vf}
pwn.college{H7ih3GawFZBjX8diIWs6XoCeWRb1IllGZOSzqflxx0lwoZ}
pwn.college{JjmJdsfOZOuCCDZYqM9BiLlvfdvfcaOCKfB-gl5iSsx5GI}
pwn.college{moes9-ffB-RdBuSqmp.NnZhsk14cm0DUAnGoofkOT9EeFL}
pwn.college{5nGCvs9eCoSIcl6d4a0yvahXAZzt-vz.762dgX2JXO2zOn}
pwn.college{Qw5oiw4Pvm9QLBsf23v054PXBMLJuXFi7j.txS1ahRssur}
pwn.college{UVniit7QgwoCyv7eP8fQEctcCTZddn.2ozouHx9s7waKGF}
pwn.college{tcrSfwlXTtE8OgJ0DrqnkJmw-4TAaH.KgNT4DVmxlw7UDn}
pwn.college{QCP5.IuQtCjekDBYyQaf.Of9cD3dqtuxkYqAya1NMfSeE.}
pwn.college{-zTNMUwQZ6Rn0zp3cOeTL3-rfD2F6uoAUInro60sL.yffu}
pwn.college{dS13G8skrqAxk4.IPa7feOLyhDWxRIsF21-B4YcM4Z67lG}
pwn.college{vIqJgbz36ke6c-HFykXCaoCCa-ObfPtnI3rG9mbGgYLn06}
pwn.college{KHLdFvfsUHpmU1axWDglraM.cUaprlutHEyLiVATDz1-cG}
pwn.college{-tYqlKNgOkXCeaMXsnNSRSHT1JJpuIPbH3LL4jnXliMf0z}
pwn.college{Jlda4tbRoGDOf42Z63oT7mguJIev6C30v6Fnz4lTpPUYYM}
pwn.college{o9cPZfR-bTfJTlTU-829DST6wHU.QX0MzM4EDLzcTN0czW}
^Z
[1]+  Stopped                 cat /tmp/flag_fifo
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{o9cPZfR-bTfJTlTU-829DST6wHU.QX0MzM4EDLzcTN0czW}
^Z
[2]+  Stopped                 cat /tmp/flag_fifo
hacker@processes~killing-misbehaving-processes:~$ 

```

# 5. Suspending Processes

**Flag:**    
pwn.college{s75Z7QOroF20Umfw_4C1GYR15xE.dVDN4QDLzcTN0czW}

**Procedure:**      
I had to first run /challenge/run then suspend it in the background so that when I run it again it can see it's copy running and give the flag.

**Code:**        
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         401     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         403     401  0 21:47 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         401     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         531     159  0 21:47 pts/0    00:00:00 bash /challenge/run
root         533     531  0 21:47 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{s75Z7QOroF20Umfw_4C1GYR15xE.dVDN4QDLzcTN0czW}
```

# 6. Resuming Processes

**Flag:**    
pwn.college{8zoVnCroHpEpdp0B-ivVGV0V_wm.dZDN4QDLzcTN0czW}

**Procedure**   
Here I had to first run /challenge/run then suspend it in the background using Ctrl+z and then resume it using fg .

**Code:**
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{8zoVnCroHpEpdp0B-ivVGV0V_wm.dZDN4QDLzcTN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

# 7. Backgrounding Processes

**Flag:**      
pwn.college{sHMcBvGJDYlYMx_sYz0Bzi7Hmw2.ddDN4QDLzcTN0czW}

**Procedure:**       
Here I first ran /challenge/run then suspended it in the background then resumed it after that ran another run so I could get the flag.

**Code:**     
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         424 S+   bash /challenge/run
root         426 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         424 S    bash /challenge/run
root         509 S    sleep 6h
root         576 S+   bash /challenge/run
root         578 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sHMcBvGJDYlYMx_sYz0Bzi7Hmw2.ddDN4QDLzcTN0czW}
hacker@processes~backgrounding-processes:~$ 
```

# 8. Foregrounding Processes

**Flag:**     
pwn.college{Aao3M4-lJvJZZfZXWdRLB_Ero65.dhDN4QDLzcTN0czW}

**Procedure:**    
This challenge required me to run /challenge/run then suspend it resume it in background using bg and finally foreground it using fg .

**Code:**    
```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{Aao3M4-lJvJZZfZXWdRLB_Ero65.dhDN4QDLzcTN0czW}
```

# 9. Starting Background Processes

**Flag:**       
pwn.college{siFR9tTn4opoNJpztCMmvzvMPKl.dlDN4QDLzcTN0czW}

**Procedure:**      
Here I had to just start the function right backgrounded.

**Code:**      
```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 399
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{siFR9tTn4opoNJpztCMmvzvMPKl.dlDN4QDLzcTN0czW}
```

# 10. Process exit codes

**Flag:**     
pwn.college{Q0E1YYvqc2zJhbNj_M3bEO2awNC.dljN4UDLzcTN0czW}

**Procedure:**    
Here I had to run /challenge/get-code then use the code which I got from it and use it as instructed to get the flag.

**Code:**   
```bash
hacker@processes~process-exit-codes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 22:22 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 22:22 ?        00:00:00 /run/dojo/bin/sleep 6h
hacker        75       1  3 22:22 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry.js --auth=none --bind
hacker        96      75 26 22:22 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/out/node/entry
hacker       137      96 11 22:22 ?        00:00:01 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vsc
hacker       152      96  4 22:22 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/bootstrap-fork --type
hacker       215     152  0 22:22 pts/1    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workbench/contrib/terminal/browser/media/shellIntegrati
hacker       264     215  0 22:23 pts/1    00:00:00 ps -ef
hacker@processes~process-exit-codes:~$ /challenge/get-code 
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
226
hacker@processes~process-exit-codes:~$ /challenge/submit-code
You must run /challenge/submit-code with the exit code you retrieved from 
/challenge/get-code as the first argument:

Usage: /challenge/submit-code [EXIT_CODE]
hacker@processes~process-exit-codes:~$ /challenge/226
bash: /challenge/226: No such file or directory
hacker@processes~process-exit-codes:~$ /challenge/submit-code 226
CORRECT! Here is your flag:
pwn.college{Q0E1YYvqc2zJhbNj_M3bEO2awNC.dljN4UDLzcTN0czW}
```