# UNIX and Bash basics for trainee students
This repository is meant to introduce trainee students of the MoZoo Lab of the University of Bologna to the Bash environment and as a general reference to retrieve most common commands used in bioinformatics.

**Enjoy!**

**Table of contents**
  - [UNIX, Linux and Bash: let's make things clear](#unix-linux-and-bash-lets-make-things-clear)
    - [UNIX is a family of operating systems](#unix-is-a-family-of-operating-systems)
    - [GNU/Linux is a UNIX-like operating system](#gnulinux-is-a-unix-like-operating-system)
    - [The shell is a command-line interpreter](#the-shell-is-a-command-line-interpreter)
    - [Bash is a UNIX shell and a command language](#bash-is-a-unix-shell-and-a-command-language)
  - [Login to a remote machine (ssh)](#login-to-a-remote-machine-or-server)
  - Basic commands to manage files and directories (mkdir, cd, pwd, mv, cp, gzip, tar,...)
  - Bash scripting (|, >, &&, ||, variables, for cycle, if statements, while cycle,...)
  - Find, find and replace and working with "tables" (grep, sed, awk)
  - Working with conda environments
  - Working in screen sessions
  - Working with git (git clone, git push, git pull, git add,...)
    

## Useful textbooks
  - [*Unix in a nutshell*](https://www.oreilly.com/library/view/unix-in-a/0596100299/) by Arnold Robbins (2005), O'Reilly Media, Inc.
  - [*Bioinformatics data skills*](https://www.oreilly.com/library/view/bioinformatics-data-skills/9781449367480/) by Vince Buffalo (2015), O'Reilly Media, Inc.

## UNIX, Linux and Bash: let's make things clear
When first approaching bioinformatics, biologists may tend to confuse and use indiscriminately the words "Unix", "Linux" and "Bash". However, each of them refers to *different concepts*.

### UNIX is a family of operating systems
Basically, **UNIX** is a registered trademark of [The Open Group](https://www.opengroup.org/unix-systems) that refers to all the operating systems (OSs) in compliance with certain standards. In particular, all of the UNIX systems *derive directly* from the original Unix system developed at the beginning of the 70s at AT&T Bell Labs: therefore, it's better to say that **UNIX is a family of OSs**. Conversely, all the OSs that are *inspired by* but are *not fully compliant* with UNIX are called **UNIX-like** systems.

<p align="center">
<img src="https://user-images.githubusercontent.com/72141380/196491582-25707e7a-bf73-4d3f-8944-042210dcc889.png" height="100">
</p>

Two popular examples of UNIX systems are [Solaris](https://www.oracle.com/solaris/solaris11/) and [AIX](https://www.ibm.com/products/aix), while two popular examples of UNIX-like systems are [GNU/Linux](https://www.gnu.org/gnu/linux-and-gnu.html) and MacOS X (the most recent Apple systems). Two examples of non-UNIX systems are Windows and AppleDOS/MacOS (the very first Apple's systems).

### GNU/Linux is a UNIX-like operating system
So now you should have also understood what is Linux (or better, GNU/Linux). **GNU/Linux** is (another) OS of the **UNIX-like family** and is the result of the fusion of the Linux and the GNU projects (we will not discuss here the reasons behind this fusion). GNU/Linux comes nowadays with **many distributions** ("distros" in short), like **[Ubuntu](https://www.ubuntu-it.org/)** (the one you are probably going to use), [CentOS](https://www.centos.org/), [Fedora](https://getfedora.org/it/), [Debian](https://www.debian.org/index.it.html) and [Arch Linux](https://archlinux.org/).

<p align="center">
<img src="https://user-images.githubusercontent.com/72141380/196498196-681b548d-aa3a-43fe-9b0c-64b0abbe5be0.png" height="100"><img src="https://user-images.githubusercontent.com/72141380/196494926-2ad5897b-7b55-4ee4-bbca-3af8a9be4f83.png" height="100">
</p>

### The shell is a command-line interpreter
The UNIX system was originally created without any graphical interface because of technological limitations and users used to interact with their computers just by typing commands on the shell, on what is called a **command-line interpreter** (CLI; or command-line user interface). Nowadays, we don't usually use the shell to interact with our computers, as we now rely on **graphical user interfaces** (GUIs), which are simple to use and very intuitive and allow users to interact with files and directories in a multimedia environment.

<p align="center">
<img src="https://user-images.githubusercontent.com/72141380/198610525-ffc37b06-9f52-4c91-9a62-ae3ff6564c1d.png", height=80>
</p>

*So why should we use the shell to do bioinformatics?* The shell (and CLIs in general) is not as simple and intuitive to use as a GUI, but it is far more powerful. In fact, the shell allows users to accomplish very big and repetitive tasks in a very efficient and fast way, just by typing text with the keyboard and never using the mouse.

For example, imagine you want to rename all the 874 photos of flamingos and shorebirds you have taken on your last field trip in Comacchio by including the date, the place and a progressive number. If you attempt to do it by means of the GUI, even if you are very skilled with <code>Ctrl+C</code>, <code>Ctrl+V</code> and other keyboard shortcuts, the task will probably take several hours and will prevent you from spending some time with your houseplants.

On the contrary, the shell will just take few minutes of your time to do the task (you can try to think about a command to rename the photos from Comacchio later on this manual...). And obviusly, bioinformatics is basically made up of tons of files that you have to rename, modify, move and execute.

Overall, the shell (or terminal, or command-line) can just be considered as a way to interact with your computer through text-based commands. The shell is thus **a program** that is able to understand commands and allows users to interact with text files, directories, executables and everything else is stored in a computer.

Every text command you type in the shell is called the **standard input** (stdin). Every text output you are given by a command is called the **standard output** (stdout). Every error message you are given by a command is called the **standard error** (stderr). This classification will be useful when we will start to use scripts and redirection. 

### Bash is a UNIX shell and a command language
Many UNIX shells exhist nowadays, but the most popular is the **B**ourne-**A**gain **Sh**ell (**Bash**), a replacement of the original Bourne shell (sh). Bash is essentially a command and programming language and, as such, it uses its own syntax and grammar. So, be aware that the same command may not work in the same way between different shells (even between UNIX shells). Bash, for example, uses a dollar symbol (**<code>$</code>**) as its own prompt, that is, when the shell is ready to receive a command it will display a <code>$</code> (not by chance, the <code>$</code> is also present in the bash logo) . On the contrary, a C shell will display a <code>%</code> as a prompt.

<p align="center">
<img src="https://user-images.githubusercontent.com/72141380/199702109-62ad5c3f-72a1-438d-9752-c0dc32bd4750.png", height=100>
  </p>

## Login to a remote machine or server
When dealing with bioinformatic data, it may be very unpleasant to work in local computers (or work stations), mostly because of the great amount of computing power that is required to run several processes. This means that most of the time bioinformaticians use to work on remote machine (being them other work stations, servers or clusters), which provide large computing resources and allow to run memory-demanding tasks.

As their name suggest, remote machines must be accessed remotely. The most common way is to use the ***s**ecure **sh**ell* (SSH), which is an **encrypted**, **UNIX-ubiquitous connection**. To **connect and login** to a remote machine then just type:

```
$ ssh username@IPaddress
```
and you will be asked a password. If everything went well, then you are logged-in in your remote machine.

If you want to **log-out** from the remote machine, just press <code>[Ctrl]+[D]</code> or type:

```
$ exit
```

## Basic commands to manage files and directories
Once you have logged-in in a remote machine (or just opened the shell on your local computer), you may be wondering in which remote directory you are. To know the  exact location you are working in (i.e., the working directory), just type:

```
$ pwd
/home/filonico
```
which stands for ***p**rint **w**orking **d**irectory*. Usually, when opening the shell, you enter by default your <code>home</code> directory, which is shortened by the symbol <code>~</code>.

Now, if you want to change your working directory and navigate thourgh the directories, for example to reach the desktop of your local machine, just type:

```
$ cd /mnt/c/Users/nicol/Desktop/
```
which stands for ***c**hange **d**irectory*. Some other useful <code>cd</code> commands are:

```
#go to the parent directory
$ cd ..
#go to the previous directory
$ cd -
#go to the root directory
$ cd /
#go to the home directory
$ cd
```
Here, you can learn the difference between an **absolute path** and a **relative path**. The absolute path unambiguously defines a file or a directory. The relative path, instead, defines the path to a file or a directory *relatively to the working directory*.
