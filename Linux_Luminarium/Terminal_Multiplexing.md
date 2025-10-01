# Terminal Multiplexing 

## 1. Launching Screen

**Flag:** 
pwn.college{kPruuf49mvNAR_jULvQMcBzoUHh.QX1gjM4EDLzcTN0czW}

**Procedure:** 
Here I had to just launch screen by using the cokmand `screen`.

**Code:**
```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{kPruuf49mvNAR_jULvQMcBzoUHh.QX1gjM4EDLzcTN0czW}
```

## 2. Detaching and Attaching

**Flag:** 
pwn.college{U2S3H1Cq9Cx5uEWtlfFDJZPeLqR.QX2gjM4EDLzcTN0czW}

**Procedure:** 
I had to launch a screen and then detach from it by `pressing Ctrl+d reaeasing it and then pressing d` after I had to run `/challenge/run` which send the flag to the screen and then reattch to that screen by using command `screen -r`. 

**Code:**
```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 152.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 152.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 152.pts-0.terminal-multiplexing~detaching-and-attaching]
```

**Screen**
```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{U2S3H1Cq9Cx5uEWtlfFDJZPeLqR.QX2gjM4EDLzcTN0czW}
Yes! Flag is: pwn.college{U2S3H1Cq9Cx5uEWtlfFDJZPeLqR.QX2gjM4EDLzcTN0czW}
```

## 3. Findng Sessions

**Flag:** 
pwn.college{Q2ZYu7bQglg0mYi-Igrid1EybfS.QX3gjM4EDLzcTN0czW}

**Procedure:** 
In this challenge already some screens were runniong I had to just list them using `screen -ls` and then go through each of them to find out which one contained the correct flag.

**Code:**
```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        163.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        152.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_59d46e4580f12b8c    (Detached)
        147.session_df114f4476257c2e    (Detached)
        150.session_25c46f3098e23684    (Detached)
5 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_59d46e4580f12b8c
[detached from 144.session_59d46e4580f12b8c]
```
**Screen:**
```bash
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{Q2ZYu7bQglg0mYi-Igrid1EybfS.QX3gjM4EDLzcTN0czW}
pwn.college{Q2ZYu7bQglg0mYi-Igrid1EybfS.QX3gjM4EDLzcTN0czW}
```

## 4. Launching Screen

**Flag:** 
pwn.college{cYLiBYMD8kDbLhy2LHcWCBzo_vd.QX4gjM4EDLzcTN0czW}

**Procedure:** 
Already in this chgallenge two windows were open I had to just reattach with the screen using `screen -r` then navigate throught the screen windows using `Ctrl+A 0-1`

**Screen:**
```bash
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{cYLiBYMD8kDbLhy2LHcWCBzo_vd.QX4gjM4EDLzcTN0czW}> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{cYLiBYMD8kDbLhy2LHcWCBzo_vd.QX4gjM4EDLzcTN0czW}
```

## 5. Detaching and Attaching(tmux)

**Flag:** 
Here `tmux` was introduced i.e. terminal multiplier which is screen's younger, more modern cousin. It does all the same things but with some different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix. I had to just launch it once then detach from it run `/challenge/run` and then reattach to it to get the flag.

**Procedure:** 

**Code:**
```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]
```

**tmux:**
```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{0R34C4Tq9K0geklE58HtMFVlMkC.QX5gjM4EDLzcTN0czW}
Congratulations, here is your flag: pwn.college{0R34C4Tq9K0geklE58HtMFVlMkC.QX5gjM4EDLzcTN0czW}
```

## 5. Launching Screen

**Flag:** 
pwn.college{QWmdYhE4o7rqbebv4SEnOlP5FOx.QXwkjM4EDLzcTN0czW}

**Procedure:** 
Here I had to just switch between various windows of tmux just like in the `switching wnidows` challenge but this time in tmux, where the new prefix for all commands becomes `Ctrl+B`.

**Code:**
```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
[detached (from session challenge_session)]
```

**tmux:**
```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{QWmdYhE4o7rqbebv4SEnOlP5FOx.QXwkjM4EDLzcTN0czW}> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{QWmdYhE4o7rqbebv4SEnOlP5FOx.QXwkjM4EDLzcTN0czW}
```