# Linux Fundamentals (Part 1)

## Introduction
### Where is Linux used?

It's fair to say that Linux is a lot more intimidating to approach than Operating System's (OSs) such as Windows. Both variants have their own advantages and disadvantages. 

For example, Linux is considerably much more lightweight and you'd be surprised to know that there's a good chance you've used Linux in some form or another every day! 

Linux powers things such as:
- Websites that you visit
- Car entertainment/control panels
- Point of Sale (PoS) systems such as checkout tills and registers in shops
- Critical infrastructures such as traffic light controllers or industrial sensors
- Phones, and similar small computing devices
- And much much more!

### Deploying your first Linux machine

For the rest of the TryHackMe rooms (which use lab machines), I have already set up my own Kali Linux Virtual Machine (Oracle VirtualBox VM).

**How did I connect?**
1. On the TryHackMe website, click your profile picture  > `Manage Account` > `VM and VPN Settings` > scroll down to `openVPN`
2. Downloaded configuration file (UDP)
3. In my Kali Linux terminal: `$ openvpn [filename].ovpn` (make sure to keep terminal open)

![[Pasted image 20260902174412.png]]

4. On the TryHackMe room, deploy a lab machine, wait for an IP address to show up. (For example: `10.66.142.126`)
5. Go to Kali terminal, type `$ ping [IP_address]` (EX: `$ ping 10.66.142.126`)
6. There should be packets going through, showing that the two machines can hear each other!

![[Pasted image 20260902174513.png]]

7. Now, to connect to the actual lab machine of the room: `$ ssh tryhackme@[IP_address]` > type "yes" for fingerprint > type `tryhackme` for the fingerprint password.

![[Pasted image 20260902174622.png]]
8. Finally, you should be in `tryhackme@linux1:~$ `

![[Pasted image 20260902174656.png]]


Task 1:

Q1) *"I've deployed my machine and am ready to go"*

**ANSWER:** no answer needed.

## Talking to Linux

### Who are you in this machine?

**Linux** is a popular choice for servers and the machines that you'll interact within cyber security. 

Being familiar with the terminal (command line interface) on Linux is a critical skill as you will most likely spend most of your time here in Cyber security. From running hacking tools to hunting down attackers.

A command is an instruction that we can give the computer to perform a given task. One of the first commands we can do is `whoami`.  

> This is important in Cyber security because you will often be changing users on the machine, which determines what you can and cannot do.

| `whoami` | tells you who you are on the system |
| -------- | ----------------------------------- |

When you run your first command, you will see some text. We call this output. Interacting with Linux feels like a conversation. You give it an instruction, and it gives you output. 

We can ask Linux to output specific text for us.

| `echo` | output some specific text that is provided |
| ------ | ------------------------------------------ |

To echo the text "TryHackMe", we can use `echo TryHackMe`. For multiple words, we will need to wrap these in quotes. For example, `echo "hello world"`. 

Using `echo` is just the start of a very important skill in Cyber security: being able create output and sending it somewhere. 

Task 2:

1) *"What command would we use to find out who we are on the system?"*

ANSWER: `whoami`

2) *"What command would we use to output some text?"*

ANSWER: `echo`

## Finding Your Way Around

| `ls`  | list what's in the current folder       |
| ----- | --------------------------------------- |
| `cd`  | change directory — move into a folder   |
| `cat` | show the contents of a file             |
| `pwd` | print working directory — "where am I?" |

> On Linux, you may notice that files and folders show as different colors. This makes it easy to identify what it is. On this Linux system, folders are blue.

Task 3:

Q1) *"Run `ls` in the current folder. How many folders are there?"*

1. type `$ ls` in Kali Linux terminal
2. Count # of folders

![[Pasted image 20260902175303.png]]
**ANSWER:** 4

Q2) *"One of those folders contains a file. Which folder is it?"*

1. do `cd` command > then `ls` on each folder

> Note: doing `cd` while in a folder changes your directory to home directory!

![[Pasted image 20260902175619.png]]

**ANSWER:** `folder1`

Q3) *"Use `cat` to read the file within this folder. What does it say?"*

1. `cd folder1` > `ls` (lists out contents of folder)
2. `cat access.log` (useless)
3. `cat passwords.txt` (we get the flag!)

![[Pasted image 20260902175920.png]]

**ANSWER:** `password123`

## Let the Machine Do the Searching

| `find` | search for files by their name. For example, `find -name passwords.txt`     |
| ------ | --------------------------------------------------------------------------- |
| `grep` | searches _inside_ for text. For example, `grep "password123" passwords.txt` |
Task 4: 

Q1) *"After using `grep "THM" access.log` a flag was found. What is the flag?"*

1. go to home directory using `cd`
2. type in `grep "THM" access.log`
3. find and copy the `THM{...}` output that has been found

![[Pasted image 20260902180627.png]]

**ANSWER:** `THM{ACCESS}`

## Shell Operators (Combining Commands)

In Linux, there are a set of special characters that can combine commands together. 

These are called **"Operators"** which tell Linux how it should process both commands. 

From being able to combine commands to doing what's called a **redirection** - sending the output of commands elsewhere.

| `&`  | **Runs the command, but does not wait for it to finish before you can do anything else. The command runs in the backgorund, and is helpful for commands that might take a while to complete, or ones that you want to keep running.** |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `&&` | **Runs both commands, but waits for the first command to finish first, before the next. Like a set of dominoes.**                                                                                                                     |
| `>`  | **Used to redirect output. We can take the output of a command and send it to a file. This operator will overwrite anything that exists in the file.**                                                                                |
| `>>` | **This redirector does the same thing, but instead of overwriting, it will just add the output to the bottom of the file.**                                                                                                           |

> For example, `echo hey > welcome` makes a file named `welcome` containing "hey" in it's contents. 
> We can use `cat welcome` to verify that it worked.

Q1) *"What operator waits for the first command to finish before running the next command?"*

**ANSWER:** `&&`

Q2) "What redirector allows us to save the output of a command **without overwriting** the contents of a file?"

**ANSWER:** `>>`


