# Silly Shenanigans

## 1. Bashrc Backdoor

**Flag:**
pwn.college{EFgWtsIy0jlms17ycKmKdJNTMYn.QXxMTM3EDLzcTN0czW}

**Procedure:**
Here I had to first change the `.bashrc` of the user `zardus` then add a read command at the end of his `.bashrc`. that was `cat /flag`. Then I had to head back again to `hacker` and run `/challenge/victim` which ran the changed `.bashrc` and I got the flag. 

**Code:**
```bash
hacker@shenanigans~bashrc-backdoor:~$ cat /challenge/victim
#!/opt/pwn.college/python

import pwnlib.tubes.process
import time
import sys
import os

def slow_type(s, mask=None, to=None):
    for c in s:
        if mask:
            print(mask, end="", flush=True)
        else:
            print(c, end="", flush=True)
        if to:
            to.write(c.encode())
        time.sleep(0.1)

def cmd(p, s):
    slow_type(s, to=p)
    if not s.endswith("\n"):
        p.write(b"\n")
    p.clean()

def login(username, password):
    print("Username:", end=" ", flush=True)
    slow_type(username+"\n")
    tty = os.ttyname(1)
    p = pwnlib.tubes.process.process(
        f"""script -c "/bin/su --login {username}" -q /dev/stderr -E never >{tty}""",
        shell=True,
        stderr=pwnlib.tubes.process.STDOUT,
    )
    p.clean()
    slow_type(password+"\n", mask="*", to=p)
    p.clean()
    return p

p = login("zardus", open("/challenge/.victim_pass").read().strip())
cmd(p, "exit\n")
p.wait()
hacker@shenanigans~bashrc-backdoor:~$ nano /challenge/victim
hacker@shenanigans~bashrc-backdoor:~$ cat /challenge/victim
#!/opt/pwn.college/python

import pwnlib.tubes.process
import time
import sys
import os

def slow_type(s, mask=None, to=None):
    for c in s:
        if mask:
            print(mask, end="", flush=True)
        else:
            print(c, end="", flush=True)
        if to:
            to.write(c.encode())
        time.sleep(0.1)

def cmd(p, s):
    slow_type(s, to=p)
    if not s.endswith("\n"):
        p.write(b"\n")
    p.clean()

def login(username, password):
    print("Username:", end=" ", flush=True)
    slow_type(username+"\n")
    tty = os.ttyname(1)
    p = pwnlib.tubes.process.process(
        f"""script -c "/bin/su --login {username}" -q /dev/stderr -E never >{tty}""",
        shell=True,
        stderr=pwnlib.tubes.process.STDOUT,
    )
    p.clean()
    slow_type(password+"\n", mask="*", to=p)
    p.clean()
    return p

p = login("zardus", open("/challenge/.victim_pass").read().strip())
cmd(p, "exit\n")
p.wait()
hacker@shenanigans~bashrc-backdoor:~$ home/zardus/.bashrc
bash: home/zardus/.bashrc: No such file or directory
hacker@shenanigans~bashrc-backdoor:~$ ls /home/hacker
 COLLEGE   a       flag_fifo      not-the-flag     pwn          solve.sh   win.sh
 Desktop   b       instruction   'not-the-flag!'   pwn_output   t          x.sh
 PATH      error   instructions   output           rm.sh        the-flag
 PWN       flag    myflag         p.sh             scripts      win
hacker@shenanigans~bashrc-backdoor:~$ ls /home/zardus
hacker@shenanigans~bashrc-backdoor:~$ ls /home/zardus
hacker@shenanigans~bashrc-backdoor:~$ ls /home/
hacker  zardus
hacker@shenanigans~bashrc-backdoor:~$ cd zardus
bash: cd: zardus: No such file or directory
hacker@shenanigans~bashrc-backdoor:~$ ls
 COLLEGE   a       flag_fifo      not-the-flag     pwn          solve.sh   win.sh
 Desktop   b       instruction   'not-the-flag!'   pwn_output   t          x.sh
 PATH      error   instructions   output           rm.sh        the-flag
 PWN       flag    myflag         p.sh             scripts      win
hacker@shenanigans~bashrc-backdoor:~$ ../
bash: ../: Is a directory
hacker@shenanigans~bashrc-backdoor:~$ cd ../
hacker@shenanigans~bashrc-backdoor:/home$ cd zardus
hacker@shenanigans~bashrc-backdoor:/home/zardus$ ls
hacker@shenanigans~bashrc-backdoor:/home/zardus$ ls
hacker@shenanigans~bashrc-backdoor:/home/zardus$ find / -name ".bashrc"
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/home/zardus/.bashrc
/home/hacker/.bashrc
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.4mK6TfTSUV’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
/etc/skel/.bashrc
find: ‘/etc/ssl/private’: Permission denied
^Z
[1]+  Stopped                 find / -name ".bashrc"
hacker@shenanigans~bashrc-backdoor:/home/zardus$ nano .bashrc
hacker@shenanigans~bashrc-backdoor:/home/zardus$ cd ~/
hacker@shenanigans~bashrc-backdoor:~$ ls
 COLLEGE   a       flag_fifo      not-the-flag     pwn          solve.sh   win.sh
 Desktop   b       instruction   'not-the-flag!'   pwn_output   t          x.sh
 PATH      error   instructions   output           rm.sh        the-flag
 PWN       flag    myflag         p.sh             scripts      win
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim
Username: zardus
Password: ***********
pwn.college{EFgWtsIy0jlms17ycKmKdJNTMYn.QXxMTM3EDLzcTN0czW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```

