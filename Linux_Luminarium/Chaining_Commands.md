# 1. Chaining with Semicolons

**Flag:**    
pwn.college{osNB4N9lWjFGtuXpBJZcbpTLRfJ.dVTN4QDLzcTN0czW}

**Procedure:**    
I used ' ; ' to chain the execution statement of pwn and college in challenge.

**Code:**           
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{osNB4N9lWjFGtuXpBJZcbpTLRfJ.dVTN4QDLzcTN0czW}
```

# 2. Building on Success

**Flag:**
pwn.college{MJVX-U62PvLyYxMwsm7kBsRhFsy.QXyQzM4EDLzcTN0czW}

**Procedure:**
Here the condition was that if `/challenge/first-success` executes and terminates with exit code '0' then only `/challenge/second` should run so I did it in the following code.

**Code:**
```bash
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with 
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{MJVX-U62PvLyYxMwsm7kBsRhFsy.QXyQzM4EDLzcTN0czW}
```

# 3. Handling Failure

**Flag:**
pwn.college{00rSbqYmqsqemBz0JKXMXsEYZUZ.QXzQzM4EDLzcTN0czW}

**Procedure:**
Here I had to chai the two commands `/challenge/first-failure` and `/challenge/second` such that only one of it runs.

**Code:**
```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{00rSbqYmqsqemBz0JKXMXsEYZUZ.QXzQzM4EDLzcTN0czW}
```

# 4. Your First Shell Script

**Flag:**    
pwn.college{wd-RSiCT6jCcHQ6AN2eM8v99fge.dFzN4QDLzcTN0czW}

**Procedure:**    
Here I struggled a little in getting it that I had to use to write the execution statements in shell script x.sh and then I used bash x.sh to run it and get the flag.

**Code:**           
```bash
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{wd-RSiCT6jCcHQ6AN2eM8v99fge.dFzN4QDLzcTN0czW}
```

# 5. Redirecting Script Output

**Flag:**    
pwn.college{YgAddJzJwz1RfLil4v9Nrx2inU8.dhTM5QDLzcTN0czW}

**Procedure:**    
Here first I created and edited the shell script p.sh and wrote the commands '/challenge/pwn' and '/challenge/college' and then piped the output to /challenge/solve.

**Code:**           
```bash
hacker@chaining~redirecting-script-output:~$ nano p.sh
hacker@chaining~redirecting-script-output:~$ bash p.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{YgAddJzJwz1RfLil4v9Nrx2inU8.dhTM5QDLzcTN0czW}
```

# 6. Executable Shell Scripts

**Flag:**    
pwn.college{Am7DzFA7GPKu4WL0VpIaQW8Mkxl.dRzNyUDLzcTN0czW}

**Procedure:**    
This challenge required me to creat a shell script with /challenge/solve in it so that I can invoke it while execution that script but this time I could not use bash so I had to make 
the script executable using chmod command and then executed it using it's relative path.

**Code:**           
```bash
hacker@chaining~executable-shell-scripts:~$ nano p.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x p.sh
hacker@chaining~executable-shell-scripts:~$ ./p.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Am7DzFA7GPKu4WL0VpIaQW8Mkxl.dRzNyUDLzcTN0czW}
```

# 7. Understanding Shebangs 

**Flag:** 
pwn.college{EDSaJ7SSXBNeG-yytADm-IIfinz.QX5MzM4EDLzcTN0czW}

**Procedure:**
Here I first made a script named `solve.sh` in which I wrote `echo "hack the planet"` then I ran `/challenge/run` to verify that it works to get the flag.

**Code:**
```bash
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ ./solve
bash: ./solve: No such file or directory
hacker@chaining~understanding-shebangs:~$ ./solve.sh
bash: ./solve.sh: Permission denied
hacker@chaining~understanding-shebangs:~$ chmod +x solve.sh
hacker@chaining~understanding-shebangs:~$ ./solve.sh
hack the planet
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{EDSaJ7SSXBNeG-yytADm-IIfinz.QX5MzM4EDLzcTN0czW}
```

# 8. Scripting wwith Arguments

**Flag:** 
pwn.college{AORx5TKW2uxPbq-2fmc-036T7c0.QX1MzM4EDLzcTN0czW}

**Procedure:**
Here I had to create a script which accepts two arguments prints the second argument first then the first argument. I did it using `read`. I did try using `read` way earlier but I don't know what was his problem and suddenly when I again gave it a try with `read` it worked. Oh I got it why it happened, bcz I was earlier printing `Second argument: $2 First argument: $1` instead it just wanted the output as `$2 $1`.(Uselessly time waste I did on this🤡)

**Code:**
```bash
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod +x solve.sh
hacker@chaining~scripting-with-arguments:~$ ./solve.sh
Second Argument : 
first Argument : 
hacker@chaining~scripting-with-arguments:~$ ./solve.sh hello world
Second Argument : world
first Argument : hello
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_V74ntv808As pwn_SwuS9TZKWPA
Got: Second Argument : college_V74ntv808As
first Argument : pwn_SwuS9TZKWPA
hacker@chaining~scripting-with-arguments:~$ /challenge/run pwn college
Not quite right!
Expected: college_DsVDco4Exp0 pwn_VBZRvhkAw0w
Got: Second Argument : college_DsVDco4Exp0
first Argument : pwn_VBZRvhkAw0w
hacker@chaining~scripting-with-arguments:~$ /challenge/run college pwn
Not quite right!
Expected: college_11cDLZAFJwo pwn_Y8N1zogWztY
Got: Second Argument : college_11cDLZAFJwo
first Argument : pwn_Y8N1zogWztY
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/ru
bash: /challenge/ru: No such file or directory
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_Q1b9UbKI2M pwn_3tBBh4c5kM
Got: /home/hacker/solve.sh: line 2: pwn_3tBBh4c5kM: command not found
Second Argument : college_Q1b9UbKI2M
first Argument : pwn_3tBBh4c5kM
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ ./solve.sh hello world
./solve.sh: line 2: hello: command not found
Second Argument : world
first Argument : hello
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ ./solve.sh hello world
hello world
world
Second Argument : world
first Argument : hello
hacker@chaining~scripting-with-arguments:~$ /challenge/run
hello
world
Not quite right!
Expected: college_mUXmjjLBz4 pwn_DZtF2kuxKgg
Got: Second Argument : college_mUXmjjLBz4
first Argument : pwn_DZtF2kuxKgg
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_9enkXR0ZzA0 pwn_zoHm0BITdBI
Got: Input: pwn_zoHm0BITdBI college_9enkXR0ZzA0
Second Argument : college_9enkXR0ZzA0
first Argument : pwn_zoHm0BITdBI
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_fI3yVz6tNg pwn_dJLO9kmbNio
Got: Input: pwn_dJLO9kmbNio college_fI3yVz6tNg
college_fI3yVz6tNg #1
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_b6d1sOmScU pwn_SFScknYVT0
Got: Input: pwn_SFScknYVT0 college_b6d1sOmScU
college_b6d1sOmScU pwn_SFScknYVT0
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
hello 
world
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{AORx5TKW2uxPbq-2fmc-036T7c0.QX1MzM4EDLzcTN0czW}
```

# 9. Scripting with Conditionals

**Flag:** 
pwn.college{EBaPmw0uFpTzMBJgzq7j2gN9a8n.QX2MzM4EDLzcTN0czW}

**Procedure:**
This one was easier from the last one as it was clearly stated what way it wanted it's output that iff "pwn" is entered then only output "college".

**Code:**
```bash
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{EBaPmw0uFpTzMBJgzq7j2gN9a8n.QX2MzM4EDLzcTN0czW}
```

# 10. Scripting with Default Cases 

**Flag:** 
pwn.college{IiY9lZzdcNUDum6IgEFCZ9F_W9Z.QX3MzM4EDLzcTN0czW}

**Procedure:**
Continuation of previous challenge just has=d to add an else case which outputs "nope" if "pwn" is not entered.

**Code:**
```bash
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{IiY9lZzdcNUDum6IgEFCZ9F_W9Z.QX3MzM4EDLzcTN0czW}
```

# 11. Scripting with Multiple Conditions

**Flag:** 
pwn.college{0gSM5v93KREOpN5t29sxr_TB8XF.QX4MzM4EDLzcTN0czW}

**Procedure:**
Continuation of previous challenge but now the conditions were<br>
-Takes one argument<br>
-If the argument is "hack", output "the planet"<br>
-If the argument is "pwn", output "college"<br>
-If the argument is "learn", output "linux"<br>
-For any other input, output "unknown"<br>

**Code:**
```bash
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{0gSM5v93KREOpN5t29sxr_TB8XF.QX4MzM4EDLzcTN0czW}
```

# 12. Reading Shell Scripts 

**Flag:** 
pwn.college{Agjl0_DuWYNhHdIv4dwg8Zh0CN9.QXyADO4EDLzcTN0czW}

**Procedure:**
I had to just read out the script `/challenge/run` and I got to know the password for printing the flag is `hack the PLANET` so I enterted it and got the flag.

**Code:**
```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{Agjl0_DuWYNhHdIv4dwg8Zh0CN9.QXyADO4EDLzcTN0czW}
```
