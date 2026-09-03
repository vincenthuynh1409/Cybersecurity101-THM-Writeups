# Linux Fundamentals (Part 2)

## Introduction

In **Linux Fundamentals part 2**, we'll be ditching the in-browser functionality and help you get started in what is a fundamental skill in being able to login to and control the terminals of remote machines. 

**Not only this, but the room will also have you:**
- Unlocking the potential of your first few commands by introducing you to using flags and arguments
- Advancing your knowledge of the filesystem to perform some more useful commands such as copying and moving files
- Discovering how access to files and folders is managed and how we can determine our access.

Task 1:

Q1) *"Let's proceed!"*

**ANSWER:** No Answer Needed

<br>

## Accessing Your Linux Machine Using SSH

### What is SSH & how Does it Work?

**Secure Shell (SSH)** = protocol between devices in an encrypted form. 

Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network --> where it is then unencrypted once it reaches the remote machine, such as in the diagram below.

![](https://cdn-images.tryhackme.com/user-uploads/5c549500924ec576f953d9fc/room-content/154f110d35efe47d493df29cdb773109.svg)

- SSH allows us to remotely execute commands on another device remotely.
- Any data sent between the devices is encrypted when it is sent over a network such as the Internet

Task 2:

Q1) *"I've logged into the Linux Fundamentals Part 2 machine using SSH!"*

1. Open Kali Linux VM terminal
2. Type `ssh tryhackme@[IP_address]`
3. Password = `tryhackme`
4. You're in.


<img width="567" height="714" alt="image" src="https://github.com/user-attachments/assets/abcfaa7c-5dc4-4a65-b51b-027d44ae1b84" />


**ANSWER:** No answer needed

<br>

## Introduction to Flags and Switches

### Flags and Switches

A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.

We'll later discuss how we can identify what commands allow for arguments to be provided and understanding what these do exactly.

When using a command, unless otherwise specified, it will perform its default behaviour. For example, `ls` lists the contents of the working directory. However, hidden files are not shown. We can use flags and switches to extend the behaviour of commands.

Using our `ls` example, `ls` informs us that there is only one folder named "folder1" as highlighted in the screenshot below. Note that the contents in the screenshots below are only examples.

Using ls to view the contents of a directory

```bash
tryhackme@linux2:~$ ls
folder1
tryhackme@linux2:~$
```

However, after using the `-a` argument (short for `--all`), we now suddenly have an output with a few more files and folders such as ".hiddenfolder". Files and folders with "**.**" are hidden files.

Using ls to view hidden folders

```shell
tryhackme@linux2:~$ ls -a 
.hiddenfolder folder1
tryhackme@linux2:~$
```

Commands that accept these will also have a `--help` option. This option will list the possible options that the command accepts, provide a brief description and example of how to use it.

Listing the options we can use with ls

```shell
tryhackme@linux2:~$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
                               e.g., '--block-size=M'; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
                               with -l: show ctime and sort by name;
                               otherwise: sort by ctime, newest first
  -C                         list entries by columns
      --color[=WHEN]         colorize the output; WHEN can be 'always' (default
                               if omitted), 'auto', or 'never'; more info below
  -d, --directory            list directories themselves, not their contents
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append '*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
tryhackme@linux2:~$
```

This option is, in fact, a formatted output of what is called the man page (short for manual), which contains documentation for Linux commands and applications.

### The MANual Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself

To access this documentation, we can use the `man` command and then provide the command we want to read the documentation for. Using our ls example, we would use `man ls` to view the manual pages for `ls` like so:

Listing the options we can use with `ls`:

```shell
tryhackme@linux2:~$ man ls
LS(1)                                               User Commands                                               LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about the FILEs (the current directory by default).  Sort entries alphabetically if none of
       -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..

       --author
              with -l, print the author of each file

       -b, --escape
              print C-style escapes for nongraphic characters

       --block-size=SIZE
              with -l, scale sizes by SIZE when printing them; e.g., '--block-size=M'; see SIZE format below

 Manual page ls(1) line 1 (press h for help or q to quit)
```

Task 3:

Q1) *"Explore the manual page of the ls command"*

**ANSWER:** No answer needed

Q2) *"What directional arrow key would we use to navigate down the manual page?"*

**ANSWER:** down

Q3) *"What flag would we use to display the output in a "human-readable" way?"*

**ANSWER:** `-h`

<br>

## Filesystem Interaction Continued

### Filesystem Commands

We covered some of the most fundamental commands when interacting with the filesystem on the Linux machine. For example, we covered how to list and find the contents of folders using `ls` and `find` and navigating the filesystem using `cd`. 

We're going to learn some more commands for interacting with the filesystem to allow us to:
- create files and folders
- move files and folders
- delete files and folders

More specifically, the following commands:

| Command | Full Name      | Purpose                      |
| ------- | -------------- | ---------------------------- |
| `touch` | touch          | Create file                  |
| `mkdir` | make directory | Create a folder              |
| `cp`    | copy           | Copy a file or folder        |
| `mv`    | move/rename    | Move/Rename a file or folder |
| `rm`    | remove         | Remove a file or folder      |
| `file`  | file           | Determine the type of a file |

_Protip: Similarly to using cat, we can provide full file paths, i.e. directory1/directory2/note for all of these commands_

  

### Creating Files and Folders (`touch`, `mkdir`)

Creating files and folders on Linux is a simple process. First, we'll cover creating a file. The touch command takes exactly one argument -- the name we want to give the file we create. For example, we can create the file "note" by using `touch note`. It's worth noting that touch simply creates a blank file. You would need to use commands like echo or text editors such as nano to add content to the blank file.

Using touch to create a new file

```shell
tryhackme@linux2:~$ touch note
tryhackme@linux2:~$ ls           
folder1 note
```

This is a similar process for making a folder, which just involves using the `mkdir` command and again providing the name that we want to assign to the directory. For example, creating the directory "mydirectory" using `mkdir mydirectory`.

Creating a new directory with mkdir

```shell
tryhackme@linux2:~$ mkdir mydirectory
tryhackme@linux2:~$ ls           
folder1 mydirectory note
```

  

### Removing Files and Folders (`rm`)

`rm` is extraordinary out of the commands that we've covered so far. You can simply remove files by using `rm`. However, you need to provide the `-R` switch alongside the name of the directory you wish to remove.

Using rm to remove a file

```shell
tryhackme@linux2:~$ rm note
tryhackme@linux2:~$ ls           
folder1 mydirectory
```

Using rm recursively to remove a directory

```shell
tryhackme@linux2:~$ rm -R mydirectory
tryhackme@linux2:~$ ls           
folder1
```

  

### Copying and Moving Files and Folders (`cp`, `mv`)

Copying and moving files is an important functionality on a Linux machine. Starting with `cp`, this command takes two arguments:

1. the name of the existing file

2. the name we wish to assign to the new file when copying

`cp` copies the entire contents of the existing file into the new file. In the screenshot below, we are copying "note" to "note2".

Using cp to copy a file

```shell
tryhackme@linux2:~$ cp note note2
tryhackme@linux2:~$ ls           
folder1 note note2
```

Moving a file takes two arguments, just like the cp command. However, rather than copying and/or creating a new file, `mv` will merge or modify the second file that we provide as an argument. Not only can you use `mv` to move a file to a new folder, but you can also use `mv` to rename a file or folder. For example, in the screenshot below, we are renaming the file "note2" to be named "note3". "note3" will now have the contents of "note2". 

Using mv to move a file

```Shell
tryhackme@linux2:~$ mv note2 note3
tryhackme@linux2:~$ ls           
folder1 note note3
```

  

### Determining File Type

What is often misleading and often catches people out is making presumptions from files as to what their purpose or contents may be. Files usually have what's known as an extension to make this easier. For example, text files usually have an extension of ".txt". But this is not necessary.

So far, the files we have used in our examples haven't had an extension. Without knowing the context of why the file is there -- we don't really know its purpose. Enter the `file` command. This command takes one argument. For example, we'll use `file` to confirm whether or not the "note" file in our examples is indeed a text file, like so `file note`.

Using file to determine the contents of a file

```Shell
tryhackme@linux2:~$ file note
note: ASCII text
```

Task 4:

Q1) *"How would you create the file named "newnote"?"*

**ANSWER:** `touch newnote`

Q2) *"On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?"*

<img width="918" height="208" alt="image" src="https://github.com/user-attachments/assets/3c774b56-a648-457e-903a-b8fe3a1b8c3e" />


**ANSWER:** `ASCII text`

Q3) *"How would we move the file "myfile" to the directory "myfolder"?"*

**ANSWER:** `mv myfile myfolder`

Q4) *"What are the contents of this file?"*

<img width="920" height="262" alt="image" src="https://github.com/user-attachments/assets/b04ae8a2-7977-4e93-9800-72930753e926" />


**ANSWER:** `THM{FILESYSTEM}`

Q5) *"Continue to apply your knowledge and practice the commands from this task."*

**ANSWER:** No answer needed

<br>

## Permissions 101

As you would have already found out by now, certain users cannot access certain files or folders. We've previously explored some commands that can be used to determine what access we have and where it leads us. 

In our previous tasks, we learned how to extend the use of commands through flags and switches. Take, for example, the `ls` command, which lists the contents of the current directory. When using the `-l` switch, we can see ten columns such as in the screenshot below. However, we're only interested in the first three columns:

Using `ls -lh` to list the permissions of all files in the directory

```shell
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
```

Although intimidating, these three columns are very important in determining certain characteristics of a file or folder and whether or not we have access to it. 

A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action -- such as the following:
- Read
- Write
- Execute

The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user -- compromising the security of every other customer. 

We'll learn the commands necessary to switch between users below.

### Switching Between Users

Switching between users on a Linux install is easy work thanks to the `su` command. Unless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:

- The user we wish to switch to
- The user's password

The `su` command takes a couple of switches that may be of relevance to you. For example, executing a command once you log in or specifying a specific shell to use. I encourage you to read the man page for `su` to find out more. However, I will cover the `-l` or `--login` switch.

Simply, by providing the `-l` switch to `su`, we start a shell that is much more similar to the actual user logging into the system - we inherit a lot more properties of the new user, i.e., environment variables and the likes.  

Using su to switch to user2 interactively

```shell-session
tryhackme@linux2:~$ su user2
Password:
user2@linux2:/home/tryhackme$
```

For example, when using `su` to switch to "user2", our new session drops us into our previous user's home directory.  

Using su to switch to user2 interactively

```shell-session
tryhackme@linux2:~$ su -l user2
Password:
user2@linux2:~$ pwd
user2@:/home/user2$
```

Where now, after using `-l`, our new session has dropped us into the home directory of "user" automatically. 

### Understanding File Permissions in Numeric Format

In Linux, every file and directory has a set of permissions that control who can read, write, or execute it. These permissions are often displayed in **symbolic format**, such as:

```bash
rwxrwxrwx
```

This format is split into three groups:

|Section|Applies To|Example|
|---|---|---|
|First 3|Owner|`rwx`|
|Next 3|Group|`rwx`|
|Last 3|Others|`rwx`|

Each letter represents a specific permission:

- `r` = read
- `w` = write
- `x` = execute

### Converting Symbolic Permissions to Numbers

Each permission has a numeric value:

|Permission|Value|
|---|---|
|Read (`r`)|4|
|Write (`w`)|2|
|Execute (`x`)|1|

To calculate the numeric value, we **add** the values together for each group.

### Example: `rwxrwxrwx`

Break it down:

|Group|Permissions|Calculation|Value|
|---|---|---|---|
|Owner|`rwx`|4 + 2 + 1|7|
|Group|`rwx`|4 + 2 + 1|7|
|Others|`rwx`|4 + 2 + 1|7|

So:

```bash
rwxrwxrwx = 777
```

### More Common Examples

|Symbolic|Numeric|Meaning|
|---|---|---|
|`rwxr-xr-x`|755|Owner can do everything, others can read and execute|
|`rw-r--r--`|644|Owner can read/write, others can only read|
|`rwx------`|700|Only the owner has access|

### Why This Matters

Understanding numeric permissions is important because:

- Many Linux commands use numeric values (e.g. `chmod 755 file`)
- You can quickly identify security risks
- You can control who can access sensitive files

For example:

```bash
chmod 750 system_overview.txt
```

This means:
- Owner: full access
- Group: read + execute
- Others: no access

Task 5:

Q1) *On the deployable machine, who is the owner of "important"?*

1. type `ls -lh` in the terminal
2. find owner of the file `important`

<img width="916" height="199" alt="image" src="https://github.com/user-attachments/assets/9704c6e6-d11e-4409-9369-b9ac511aa5e6" />


**ANSWER:** `user2`

Q2) *What would the command be to switch to the user "user2"?*

**ANSWER:** `su user2`

Q3) *Now switch to this user "user2" using the password "user2"*

<img width="916" height="106" alt="image" src="https://github.com/user-attachments/assets/101c0448-7f40-4160-bb75-2202837077ed" />


**ANSWER:** No answer needed

Q4) *Output the contents of "important", what is the flag?*

1. type `ls` to see the contents of the home directory
2. output contents of file `important` by typing `cat important`

<img width="922" height="187" alt="image" src="https://github.com/user-attachments/assets/4d49d5a3-7da4-4a66-a401-ebff0bcc2a5c" />


**ANSWER:** `THM{SU_USER2}`

<br>

## Common Directories

### /etc

This root directory is one of the most important root directories on your system. The etc folder (short for etcetera) is a commonplace location to store system files that are used by your operating system. 

For example, the sudoers file highlighted in the screenshot below contains a list of the users & groups that have permission to run `sudo` or a set of commands as the root user.

Also highlighted below are the "**passwd**" and "**shadow**" files. These two files are special for Linux as they show how your system stores the passwords for each user in encrypted formatting called sha512.

Some notable contents of the /etc directory

```shell
tryhackme@linux2:/etc$ ls
shadow passwd sudoers sudoers.d
```

## /var

The "/var" directory, with "var" being short for variable data,  is one of the main root folders found on a Linux install. This folder stores data that is frequently accessed or written by services or applications running on the system. For example, log files from running services and applications are written here (**/var/log**), or other data that is not necessarily associated with a specific user (i.e., databases and the like).

Some notable contents of the /var directory

```shell
tryhackme@linux2:/var$ ls
backups log opt tmp
```

## /root

Unlike the **/home** directory, the **/root** folder is actually the home for the "root" system user. There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user. But, it is worth a mention as the logical presumption is that this user would have their data in a directory such as "**/home/root**" by default.  

Some notable contents of the /root directory

```shell
root@linux2:~# ls
myfile myfolder passwords.xlsx
```

### /tmp

This is a unique root directory found on a Linux install. Short for "temporary", the /tmp directory is volatile and is used to store data that is only needed to be accessed once or twice. Similar to the memory on your computer, once the computer is restarted, the contents of this folder are cleared out.

What's useful for us in pentesting is that any user can write to this folder by default. Meaning once we have access to a machine, it serves as a good place to store things like our enumeration scripts.

Some notable contents of the /tmp directory

```shell
root@linux2:/tmp# ls
todelete trash.txt rubbish.bin
```


Task 6:

Q1) *Read me!*

**ANSWER:** No answer needed

Q2) *What is the directory path that would we expect logs to be stored in?*

**ANSWER:** `/var/log`

Q3) *What root directory is similar to how RAM on a computer works?*

**ANSWER:** `/tmp`

Q4) *Name the home directory of the root user*. 

**ANSWER:** `/root`

Q5) *Now apply your learning and navigate through these directories on the deployed Linux machine.*

**ANSWER:** No answer needed
