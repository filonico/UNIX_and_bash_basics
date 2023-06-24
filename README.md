# UNIX and Bash basics for trainee students
This repository is meant to introduce trainee students of the EVO•COM group of the University of Bologna to the Bash environment and as a general reference to retrieve most common commands used in bioinformatics.

**Enjoy!**

## Table of contents
  - **[Command cheat sheet](#command-cheat-sheet)**
  - **[Useful textbooks and resources](#useful-textbooks-and-resources)**
  - **[UNIX, Linux and Bash: let's make things clear](#unix-linux-and-bash-lets-make-things-clear)**
    - [UNIX is a family of operating systems](#unix-is-a-family-of-operating-systems)
    - [GNU/Linux is a UNIX-like operating system](#gnulinux-is-a-unix-like-operating-system)
    - [The shell is a command-line interpreter](#the-shell-is-a-command-line-interpreter)
    - [Bash is a UNIX shell and a command language](#bash-is-a-unix-shell-and-a-command-language)
  - **[<code>ssh</code> to login to a remote machine](#login-to-a-remote-machine-or-server)**
  - **[Basic commands to manage directories and files](#basic-commands-to-manage-directories-and-files)**
    - [<code>pwd</code>, <code>cd</code> and <code>mkdir</code> to manage directories](#pwd-cd-and-mkdir-to-manage-directories)
    - [<code>ls</code> to see the content of a directory](#ls-to-see-the-content-of-a-directory)
    - [Flags and <code>man</code> to inspect the user manual of a command](#flags-and-man-to-inspect-the-user-manual-of-a-command)
    - [<code>cat</code>, <code>less</code>, <code>head</code> and <code>tail</code> to read file content](#cat-less-head-and-tail-to-read-file-content)
    - [<code>cp</code> and <code>mv</code> to copy/paste and cut/paste files](#cp-and-mv-to-copypaste-and-cutpaste-files)
    - [<code>gzip</code>/<code>gunzip</code> and <code>zip</code>/<code>unzip</code> to work with compressed files](#gzipgunzip-and-zipunzip-to-work-with-compressed-files)
    - [ <code>tar</code> to compress directories](#tar-to-compress-directories)
  - **[Bash scripting](#bash-scripting)**
  - **[Find patterns in files, replace them and work with tables](#find-patterns-in-files-replace-them-and-work-with-tables)**
    - [<code>grep</code> to find patterns in files](#grep-to-find-patterns-in-files)
  - **Working with conda environments**
  - **Working in screen sessions**
  - **Working with git (git clone, git push, git pull, git add,...)**

## Command cheat sheet
| Command | Meaning | Description |
| --- | --- | --- |
| [<code>man</code>](#flags-and-man-to-inspect-the-user-manual-of-a-command) | *manual* | Print the manual of a UNIX command|
| [<code>ssh</code>](#login-to-a-remote-machine-or-server) | *secure shell* | Log-in to remote machines |
| [<code>pwd</code>](#pwd-cd-and-mkdir-to-manage-directories) | *print working directory* | Print the full path of the directory you are in |
| [<code>cd</code>](#pwd-cd-and-mkdir-to-manage-directories) | *change directory* | Change your working directory |
| [<code>mkdir</code>](#pwd-cd-and-mkdir-to-manage-directories) | *make directory* | Create a new directory|
| [<code>ls</code>](#ls-to-see-the-content-of-a-directory) | *list* | Print the content of a directory |
| [<code>cat</code>](#cat-less-head-and-tail-to-read-file-content) | *concatenate* | Print the content of your file(s) to the stdout |
| [<code>less</code>](#cat-less-head-and-tail-to-read-file-content) | - | Print the content of your file a screen at a time|
| [<code>head</code>](#cat-less-head-and-tail-to-read-file-content) | - | Print the first N lines of a file to the stdout |
| [<code>tail</code>](#cat-less-head-and-tail-to-read-file-content) | - | Print the last N lines of a file to the stdout |
| [<code>cp</code>](#cp-and-mv-to-copypaste-and-cutpaste-files) | *copy* | Create a copy of a file |
| [<code>mv</code>](#cp-and-mv-to-copypaste-and-cutpaste-files) | *move* | Move a file to a new location or rename it|
| [<code>gzip</code>](#gzipgunzip-and-zipunzip-to-work-with-compressed-files) | *GNU zip* | Compress a file |
| [<code>gunzip</code>](#gzipgunzip-and-zipunzip-to-work-with-compressed-files) | *GNU unzip* | Uncompress a gzip file |
| [<code>zip</code>](#gzipgunzip-and-zipunzip-to-work-with-compressed-files) | - | Compress a file |
| [<code>unzip</code>](#gzipgunzip-and-zipunzip-to-work-with-compressed-files) | - | Uncompress a zip file |
| [<code>tar</code>](#tar-to-compress-directories) | *tape archive* | Create an archive of a directory (and compress it if desidered) |
| [<code>grep</code>](#grep-to-find-patterns-in-files) | *globally searches for regular expression and prints out*| Search for a pattern in files |

[↑ Table of contents ↑](#Table-of-contents)

## Useful textbooks and resources
  - [*Unix in a nutshell*](https://www.oreilly.com/library/view/unix-in-a/0596100299/) by Arnold Robbins (2005), O'Reilly Media, Inc.
  - [*Bioinformatics data skills*](https://www.oreilly.com/library/view/bioinformatics-data-skills/9781449367480/) by Vince Buffalo (2015), O'Reilly Media, Inc.
  - [*Bash scripting cheatsheet*](https://devhints.io/bash) by Rico Sta. Cruz.
  - Take also a look at [notes by Mariangela Iannello](https://github.com/MariangelaIannello/didattica) (bash basics, scripting and transcriptome assembly/annotation pipelines, gene differential expression) and [notes by Jacopo Martelossi](https://github.com/jacopoM28/CompOmics_Tutorship/tree/main) (bash basics, scripting, genome assembly and annotation, orthology inference)!!

[↑ Table of contents ↑](#Table-of-contents)

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

[↑ Table of contents ↑](#Table-of-contents)

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

[↑ Table of contents ↑](#Table-of-contents)

### Bash is a UNIX shell and a command language
Many UNIX shells exhist nowadays, but the most popular is the <ins>B</ins>ourne-<ins>A</ins>gain <ins>SH</ins>ell (**Bash**), a replacement of the original Bourne shell (sh). Bash is essentially a command and programming language and, as such, it uses its own syntax and grammar. So, be aware that the same command may not work in the same way between different shells (even between UNIX shells). Bash, for example, uses a dollar symbol (**<code>\$</code>**) as its own prompt, that is, when the shell is ready to receive a command it will display a <code>\$</code> (not by chance, the <code>$</code> is also present in the bash logo) . On the contrary, a C shell will display a <code>%</code> as a prompt.

<p align="center">
<img src="https://user-images.githubusercontent.com/72141380/199702109-62ad5c3f-72a1-438d-9752-c0dc32bd4750.png", height=100>
  </p>
  
[↑ Table of contents ↑](#Table-of-contents)

## <code>ssh</code> to login to a remote machine or server
When dealing with bioinformatic data, it may be very unpleasant to work in local computers (or work stations), mostly because of the great amount of computing power that is required to run several processes. This means that most of the time bioinformaticians use to work on remote machine (being them other work stations, servers or clusters), which provide large computing resources and allow to run memory-demanding tasks.

As their name suggest, remote machines must be accessed remotely. The most common way is to use the *<ins>s</ins>ecure <ins>sh</ins>ell* (SSH), which is an **encrypted**, **UNIX-ubiquitous connection**. To **connect and login** to a remote machine then just type:

```bash
$ ssh username@IPaddress
```
and you will be asked a password. If everything went well, then you are logged-in in your remote machine.

If you want to **log-out** from the remote machine, just press <code>[Ctrl]+[D]</code> or type:

```bash
$ exit
```
> Use <code>ssh</code> to login to remote machines

[↑ Table of contents ↑](#Table-of-contents)

## Basic commands to manage directories and files
### <code>pwd</code>, <code>cd</code> and <code>mkdir</code> to manage directories
Once you have logged-in in a remote machine (or just opened the shell on your local computer), you may be wondering in which remote directory you are. To know the  exact location you are working in (i.e., the working directory), just type:

```bash
$ pwd
/home/filonico
```
which stands for *<ins>P</ins>rint <ins>W</ins>orking <ins>D</ins>irectory*. Usually, when opening the shell, you enter by default your <code>home</code> directory, which is shortened by the symbol <code>~</code>.

If you want to change your working directory and navigate thourgh the directories, for example to reach the desktop of your local machine, just type:

```bash
$ cd /path/to/your/Desktop/
```
where <code>cd</code> stands for *<ins>C</ins>hange <ins>D</ins>irectory*. Some other useful <code>cd</code> commands are:

```bash
#go to the parent directory
$ cd ..

#go to the previous directory
$ cd -

#go to the root directory
$ cd /

#go to the home directory
$ cd
```
You can now understand the difference between an **absolute path** and a **relative path**. The absolute path unambiguously defines a file or a directory. The relative path, instead, defines the path to a file or a directory *relatively to the working directory*.

If you want to create a new directory in your current location just type:

```bash
$ mkdir new_directory/
```
where <code>mkdir</code> stands for *<ins>M</ins>a<ins>K</ins>e <ins>DIR</ins>ectory*.

> Use <code>pwd</code> to print the absolute path of the working directory.
> 
> Use <code>cd</code> to move to a different directory.
> 
> Use <code>mkdir</code> to create a new directory.

[↑ Table of contents ↑](#Table-of-contents)

### <code>ls</code> to see the content of a directory
Now that we have understood in which directory we are located and how to change your location, it is useful to know how to **visualize the content of the directory** itself. For this purpose, we can use <code>ls</code> to *<ins>L</ins>i<ins>S</ins>t* all the files present in a directory (by default, the working directory):
```bash
#list all the files in a directory
$ ls example_files/
Dmag.HPHG.location.gff  Dmel.mito.proteins.faa
Dmel.COI.fasta          Dmel_GCF.000001215.4_genomic.fna.gz
Dmel.mito.genome.gb

#list all the files in a directory with a Long listing format
#note that ls -s can be abbreviated with ll
$ ls -l example_files/
total 43325
drwxrwxrwx 1 filonico filonico      512 Jun 20 20:09 ./
drwxrwxrwx 1 filonico filonico      512 Jun 23 13:10 ../
-rwxrwxrwx 1 filonico filonico    44664 Jun 20 20:09 Dmag.HPHG.location.gff*
-rwxrwxrwx 1 filonico filonico      626 Jun 17 18:53 Dmel.COI.fasta*
-rwxrwxrwx 1 filonico filonico    73564 Jun 17 18:53 Dmel.mito.genome.gb*
-rwxrwxrwx 1 filonico filonico     6658 Jun 20 20:25 Dmel.mito.proteins.faa*
-rwxrwxrwx 1 filonico filonico 44235956 Jun 17 20:08 Dmel_GCF.000001215.4_genomic.fna.gz*

#list all the files in a directory with a long listing format, and sort for modification time
$ ll -t example_files/
total 43325
drwxrwxrwx 1 filonico filonico      512 Jun 23 13:10 ../
-rwxrwxrwx 1 filonico filonico     6658 Jun 20 20:25 Dmel.mito.proteins.faa*
drwxrwxrwx 1 filonico filonico      512 Jun 20 20:09 ./
-rwxrwxrwx 1 filonico filonico    44664 Jun 20 20:09 Dmag.HPHG.location.gff*
-rwxrwxrwx 1 filonico filonico 44235956 Jun 17 20:08 Dmel_GCF.000001215.4_genomic.fna.gz*
-rwxrwxrwx 1 filonico filonico      626 Jun 17 18:53 Dmel.COI.fasta*
-rwxrwxrwx 1 filonico filonico    73564 Jun 17 18:53 Dmel.mito.genome.gb*
```

Let's have a look at the output of <code>ls -l</code> (or <code>ll</code>): this listing format is quite useful when moving around folders, as it gives you a lot of information on what you are seeing (e.g., the owner of the file, its size [5th column], its time of creation [6th/7th/8th columns], etc.).

> Use <code>ls</code> to list the content of a directory.
>
> Use <code>ll</code> as a shortcut to <code>ls -l</code> to list the content of a directory using a long listing format.

[↑ Table of contents ↑](#Table-of-contents)

### Flags and <code>man</code> to inspect the user manual of a command
Here you have just been introduced to **flags** (<code>-l</code> and <code>-t</code> are all flags of <code>ls</code>, but there are many others), i.e., options that can be passed to the main program to modify its behaviour. Just by changing the various accepted flags, <code>ls</code> (or any other command with implemented flags) can accomplish different tasks.

To know all the flags available for a certain UNIX tool, you can rely on the <code>man</code> command, which will print to the stdout the *<ins>MAN</ins>ual* of your interest:
```bash
#print the manual of ls
$ man ls
```


[↑ Table of contents ↑](#Table-of-contents)

### <code>cat</code>, <code>less</code>, <code>head</code> and <code>tail</code> to read file content
Through the shell you are going to interact mainly with text files, such as fastq, fasta, vcf and gff files, so it's important for you to know how to read (and visualize) what's inside of them. There are many ways to fulfil this purpose and each of them fits with different needs.

One of the most common way to inspect a file is by using <code>cat</code>, which will **print the content of your file(s) in the stdout** ([here](example_files/Dmel.COI.fasta) is the <code>Dmel.COI.fasta</code> file):
```bash
#inspect the fasta file containing the protein sequence from the COI gene of Drosophila melanogaster 
$ cat example_files/Dmel.COI.fasta
>YP_009047267.1 cytochrome c oxidase subunit I, partial (mitochondrion) [Drosophila melanogaster]
SRQWLFSTNHKDIGTLYFIFGAWAGMVGTSLSILIRAELGHPGALIGDDQIYNVIVTAHAFIMIFFMVMP
IMIGGFGNWLVPLMLGAPDMAFPRMNNMSFWLLPPALSLLLVSSMVENGAGTGWTVYPPLSAGIAHGGAS
VDLAIFSLHLAGISSILGAVNFITTVINMRSTGISLDRMPLFVWSVVITALLLLLSLPVLAGAITMLLTD
RNLNTSFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHIISQESGKKETFGSLGMIYAMLAIGL
LGFIVWAHHMFTVGMDVDTRAYFTSATMIIAVPTGIKIFSWLATLHGTQLSYSPAILWALGFVFLFTVGG
LTGVVLANSSVDIILHDTYYVVAHFHYVLSMGAVFAIMAGFIHWYPLFTGLTLNNKWLKSHFIIMFIGVN
LTFFPQHFLGLAGMPRRYSDYPDAYTTWNIVSTIGSTISLLGILFFFFIIWESLVSQRQVIYPIQLNSSI
EWYQNTPPAEHSYSELPLLTN
```

However, <code>cat</code> can be really annoying when reading big files (e.g., the fasta file of the complete predicted proteome of *Drosophila*), since it prints the *entire* content of the file in your terminal: the output will take a lot of your time to be properly inspected and cannot even be directly manipulated.

In these cases, you would like to rely on <code>less</code>, which will **print the content of your file in a sort of a new window**. In addition, <code>less</code> does not read your file all at once, but it will read (and print) it line by line and will allow you to freely scroll the file: this means that the command will take the same amount of time to read 10-sequence-long and 27k-sequence-long fasta files. Also, <code>less</code> contains some build-in functions, such as search and highlight patterns (google will help you in this task).

<code>less</code> is particularly useful to debugging your command-line pipelines, i.e., it helps you to check step by step if the commands you want to run on your files are working properly.
```bash
#imagine you want to extract all the gene IDs of the Drosophila mitochondrial proteins from the relative fasta file
#the following command lines are just descriptive of the action we want to take
$ extract_the_headers example_files/Dmel.mito.proteins.fasta | less
$ extract_the_headers example_files/Dmel.mito.proteins.fasta | remove_unwanted_information | less
$ extract_the_headers example_files/Dmel.mito.proteins.fasta | remove_unwanted_information | convert_to_tsv_format | less
```
Both <code>cat</code> and <code>less</code> can be used also to **read gzipped files** by using their sister commands <code>zcat</code> and <code>zless</code>, respectively (we will see how to (un)compress files in a [following section](#gunzip-and-unzip-to-work-with-compressed-files)).

Sometimes you may need to read just the first or last lines of a file, for example because you just need to know the header of an output or the ending time of a certain analysis. You can then use <code>head</code> and <code>tail</code> to **print to the stdout the first and last 10 lines (default) of a file** respectively ([here](example_files/Dmel.mito.genome.gb) is the <code>Dmel.mito.genome.gb</code> file):
```bash
#you can specify the number of lines to print using the flag -n
$ head -n 32 example_files/Dmel.mito.genome.gb #print the header of the genbank file
$ tail -n 328 example_files/Dmel.mito.genome.gb #print the sequence of the genbank file

#you can use head/tail to remove the last/first N lines from a file
$ head -n -328 example_files/Dmel.mito.genome.gb #remove the last line from the genbank file
$ tail -n +2 example_files/Dmel.mito.genome.gb #remove the first comment line from the genbank file
```
> Use <code>cat</code> to print the entire content of a file to the stdout.
> 
> Use <code>less</code> to inspect a chunk of a file and scroll it.
> 
> Use <code>less</code> to debug command-line pipelines.
> 
> Use <code>head</code> to print the first N lines of a file to the stdout.
> 
> Use <code>tail</code> to print the last N lines of a file to the stdout.

[↑ Table of contents ↑](#Table-of-contents)

### <code>cp</code> and <code>mv</code> to copy/paste and cut/paste files
In bioinformatics it is usually very important to maintain one (or even more) backup copy(ies) of the files you are working with, in order to not risk to lose your work. Thus, it is advisable to **copy** the original files and **paste** them in a different location on your storage, by using:
```bash
#copy a file to a different location and keep the original name
$ cp your_file.txt /location/of/the/copy/of/your_file.txt

#copy a file to a different location and rename the copy
$ cp your_file.txt /location/of/the/copy/of/your_file_copy.txt
```
where <code>cp</code> stands obviously for *<ins>C</ins>o<ins>P</ins>y*.
  
However, the storage memory is not limitless, so sometimes it is more convenient to **cut** your files and **paste** them in a different location on your storage, by usig:
```bash
#move a file to a different location and keep the original name
$ mv your_file.txt new/location/of/your_file.txt

#move a file to a different location and rename it
$ mv your_file.txt new/location/of/your_file_new.txt

# if you do not specifiy a different directory, the file will be just renamed
$ mv your_file.txt your_file_new.txt
```
where <code>mv</code> stands for *<ins>M</ins>o<ins>V</ins>e*.
  
> Use <code>cp</code> to copy and paste files.
> 
> Use <code>mv</code> to cut and paste files or to rename them in their current directory.

[↑ Table of contents ↑](#Table-of-contents)

## <code>gzip</code>/<code>gunzip</code> and <code>zip</code>/<code>unzip</code> to work with compressed files

As we have already pointed out, bioinformatic files are often very big in size (sometimes dozens of gigabytes) while our storage capacities are often (much) more restricted. Large files are also difficult to handle when being transferred to collegues via email or other protocols. Thus, it is foundamental that you carefully store your files in a way that allows you to save as much bytes as possible.

To this purpose, you can easily **compress your files** by using <code>gzip</code>, a <ins>ZIP</ins>ping program which was originally intended for <ins>G</ins>NU users. With <code>gzip</code> you can also choose the compression ratio by specifying a number between <code>1</code> (low compression ratio) and <code>9</code> (high compression ratio; default is <code>6</code>):
```bash
#gzip your very very big file
$ gzip a_very_big_file.txt

#gzip your very very big file with a low compression ratio (and a high speed)
$ gzip -1 a_very_big_file.txt

#gzip your very very big file with a high compression ratio (and a low speed)
$ gzip -9 a_very_big_file.txt
```
Note that <code>gzip</code> compresses your file inplace, thus replacing the original uncompressed file (and appending a <code>.gz</code> extension). Can you come up with a solution to this, imaging that you want to create a new file instead of replacing the original?

Another useful command to zip file is (surprisingly) <code>zip</code>, which is meant to create compressed file with a <code>.zip</code> extension (very common in a Windows environment):
```bash
#zip your very very big file
$ zip a_zipped_file.zip a_very_big_file.txt
```
However, in this case the <code>zip</code> command will not replace your original file and thus also requires the filename of your compressed file.

Besides compressing, we may clearly also want to **uncompress** some of our files. In this case we can use the <code>gunzip</code> and <code>unzip</code> commands to work with <code>.gz</code> and <code>.zip</code> files, respectively:
```bash
#gunzip a .gz file
$ gunzip a_gzipped_file.gz

#unzip a .zip file
$ unzip a_zipped_file.zip
```

During your analyses, you will run into gzipped files basically every day. Thus, you may wonder how to use such files without uncompressing them, just to avoid typing an additional command line or because you are running out of space. Fortunately, many bash commands come with certain build-in functions to **directly handle gzipped files**, such as <code>zless</code>, <code>zcat</code> (see the [previous section](#cat-less-head-and-tail-to-read-file-content) about them), <code>zgrep</code> (we will see this command in a following section), and <code>zdiff</code> ([here](example_files/Dmel_GCF.000001215.4_genomic.fna.gz) is the <code>Dmel_GCF.000001215.4_genomic.fna.gz file</code>):
```bash
#print the entire content of a gzip file to the stdout
$ zcat example_files/Dmel_GCF.000001215.4_genomic.fna.gz
>NC_004354.4 Drosophila melanogaster chromosome X
GAATTCGTCAGAAATGAgctaaacaaatttaaatcattaaatgcGAGCGGCGAATCCGGAAACAGCAACTTCAAACCAGT
CACTCTGGCTGAACTAAATGGCCTGATAAACTCACTGGAATTAAAGAAAGCCCCAGGAACTGACAATCTTAACAACAAGA
CCATAATAAACTTACCTACAAAGGCCAgaatatatttaatacttATTTATAACAACATCCTGAGAACTGGACATTTCCCG
AACAAATGGAAGCACGCTAGCATCTCAATGATTCCCAAACCAGGGAAATCACCATTTGCTCTAAATTCATACCGCCCAAT
CAGCTTACTCTCTGGTCTTTCCAAACTACTCGAAAGAATACTACTGAAACGACTGTATGACATTGACTCTTTTGCCAAAG
CAATCCCTTCCCATCAATTTGGTTTCAGAAAGGATCATGGAGCGGAACATCAGCTGGCCAGGGTGACCCAATTTATTCTA
AAAGCTTTTGATGAAAAAGATGTCTGTTCTGCCACATTCCTTGACATTACGGAAGCCTTTGACCGAGTATGGCACGACGG
CTTGCTATATAAACTATCCAGACTCATCCCCAGATACCTATTCGACCTACTTGAAAACTATTTATCTAATAGAACCTTCT
CAGTAAGGATCGACGGTGAAACAACGTCTAGGATAGGTAATATTAGAGCAGGAGTGCCCCAGGGCAGCATACTGGGACCG
GTCCTCTACTCAATATACTCATCCGACATGCCCTATCCCATCGTAAAAGACTATATGCGTAACATATCCTTCCCTGATTA
CCACCCAACTAATATTATCTTAGCTACATATGCAGATGATACCATAATTCTTAGCCGGTCCAAATATACCAAGCTTGCGA
TCAACCTAAATCAAAACTACCTTAACGTCTTCTGTAGGTGGTCAAAAAAATGGGACATAGCaattaatgcaaaaaaaaCC
GGACACATTCTTTTCTCcctaaaaaaagaacaaactAATATATACACTCCCCCACTAATCAACGGACAAAGAGCTGCCAA
ACTAAACAAACAACGCTATCTCGGACTTATGCTAGACAGAAGACTGACCTTTTGTGCACACATGACGCTGCTAAAGGGAA
AGACTATAGCTGCATATAAAAAACTGGAATGGCTAATAGGAAAAAACAGCCACCTacccaaaaatgcaaaaattctCCTC
TGGAAGCAAATTGTCTCCCCCATCTGGCATTACGCCATAGCAATCTGGGGCTCGCTGGTATCTGACACCCAAGCAAAGAA
AATTCAAACAATGGAAAACAAATACATCAGACGAATCATAAACGCCAGCAGATACACGAGACAAGCAGACATAAGGACAA
AATATaacattaaatcatttgatGAAATTTTTGACAAAGCAAGCCAACGCTACGCCAACTCCCTCACTGACCATGAAAAC
CCTTTAATATATGACCTCCTTATCAACGCCTACAAGCCGAACAGACTGGAACTAAGCAAAAACAGATACGTCAAGCaatt
...
#print the content of a gzip file a screen at a time
$ zless example_files/Dmel_GCF.000001215.4_genomic.fna.gz
```

> Use <code>gzip</code> and <code>zip</code> to compress files into a <code>.gzip</code> or a <code>.zip</code> format, respectively.
>
> Use <code>gunzip</code> and <code>unzip</code> to uncompress files from a <code>.gzip</code> or a <code>.zip</code> format, respectively.
>
>Use <code>zcat</code>, <code>zles</code> and <code>zgrep</code> to work directly with compressed files.

[↑ Table of contents ↑](#Table-of-contents)

## <code>tar</code> to compress directories
We have just seen how we can save space up by compressing single files. But what about compressing an entire directory? What if you want to archive your recent research (now published on *Nature*) on the gene-family dynamics in hematophagous dipterans? Unfortunately, <code>gzip</code> and <code>zip</code> can basically manage only single files, so you have to rely on other utilities.

<code>tar</code> is a command that allows you to **organize a whole directory** into a single *<ins>T</ins>ape <ins>AR</ins>chive*, which can be subsequently compressed. <code>tar</code> can archive and compress a whole directory all in the same command line and you just need to specify the name of the output compressed archive and the input directory:
```bash
#archive and compress our example_files/ directory
$ tar -c -v -z -f example_files.tar.gz example_file/

#or, in short
$ tar -cvzf example_files.tar.gz example_file/
```
where <code>-c</code> instructs the command to *<ins>C</ins>reate* a new archive, <code>-v</code> instructs to be *<ins>V</ins>erbose* on the stdout, <code>-z</code> instructs to *g<ins>Z</ins>ip* the archive, and <code>-f</code> specifies the output *<ins>F</ins>ile* name.

You can use <code>tar</code> also to **un-compress and un-archive** a directory:
```bash
#archive and compress our example_files/ directory
$ tar -v -x -f example_files.tar.gz

#or, in short
$ tar -vxf example_files.tar.gz
```
where <code>-x</code> instructs the command to *e<ins>X</ins>tract* (uncompress) the gzip archive.

>Use <code>tar -cvzf</code> to compress a whole directory
>
>Use <code>tar -xzf</code> to uncompress a gzip directory
>
>Usa <code>man</code> to inspect the manual of a UNIX command

[↑ Table of contents ↑](#Table-of-contents)

# Bash scripting

|, >, &&, ||, variables, for cycle, if statements, while cycle,...

[↑ Table of contents ↑](#Table-of-contents)

# Find patterns in files, replace them and work with tables 

## <code>grep</code> to find patterns in files
We have already said multiple times that files containing biological data and analyses can be really really big (I'm probably getting boring with this kind of sentence). However, of all the lines and words stored inside a text file, you may just need few of them.

For example, let's have a look at the file [<code>Dmag.HPHG.location.gff</code>](example_files/Dmag.HPHG.location.gff). This is a so-called gff (*General Feature Format*) file, which stores informations about different genetic sequences in a genome (see [here](https://www.ensembl.org/info/website/upload/gff3.html) to know more about gffs). Imagine that you just want to extract informations about mRNA features from the gff. <code>grep</code> is the master UNIX command that accomplishes such tasks, as it ***<ins>G</ins>lobally searches for <ins>R</ins>egular <ins>E</ins>xpression and <ins>P</ins>rints out*** the results:
```bash
#extract "mRNA" feature from the gff file
$ grep "mRNA" example_files/Dmag.HPHG.location.gff
NC_046178.1     Gnomon  mRNA    7392893 7415487 .       +       .       ID=rna-XM_032930663.1;Parent=gene-LOC116924082;Dbxref=GeneID:116924082,Genbank:XM_032930663.1;Name=XM_032930663.1;gene=LOC116924082;model_evidence=Supporting evidence includes similarity to: 9 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 31 samples with support for all annotated introns;product=homeotic protein caudal-like%2C transcript variant X1;transcript_id=XM_032930663.1
NC_046178.1     Gnomon  mRNA    7993982 8009001 .       +       .       ID=rna-XM_032929649.1;Parent=gene-LOC116923174;Dbxref=GeneID:116923174,Genbank:XM_032929649.1;Name=XM_032929649.1;Note=The sequence of the model RefSeq transcript was modified relative to this genomic sequence to represent the inferred CDS: added 86 bases not found in genome assembly;exception=annotated by transcript or proteomic data;gene=LOC116923174;inference=similar to RNA sequence (same species):INSD:GGRO01024192.1;model_evidence=Supporting evidence includes similarity to: 1 2C 8 Proteins%2C and 99%25 coverage of the annotated genomic feature by RNAseq alignments;partial=true;product=homeobox protein abdominal-B-like;transcript_id=XM_032929649.1
NC_046178.1     Gnomon  mRNA    8014561 8088186 .       +       .       ID=rna-XM_032929652.1;Parent=gene-LOC116923176;Dbxref=GeneID:116923176,Genbank:XM_032929652.1;Name=XM_032929652.1;gene=LOC116923176;model_evidence=Supporting evidence includes similarity to: 1 2C 19 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 3 samples with support for all annotated introns;product=homeobox protein abdominal-A homolog%2C transcript variant X1;transcript_id=XM_032929652.1
NC_046178.1     Gnomon  mRNA    8135891 8151281 .       +       .       ID=rna-XM_032929678.1;Parent=gene-LOC116923203;Dbxref=GeneID:116923203,Genbank:XM_032929678.1;Name=XM_032929678.1;gene=LOC116923203;model_evidence=Supporting evidence includes similarity to: 1 2C 41 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 125 samples with support for all annotated introns;product=homeotic protein ultrabithorax-like;transcript_id=XM_032929678.1
NC_046178.1     Gnomon  mRNA    8151373 8173264 .       +       .       ID=rna-XM_032929672.1;Parent=gene-LOC116923197;Dbxref=GeneID:116923197,Genbank:XM_032929672.1;Name=XM_032929672.1;gene=LOC116923197;model_evidence=Supporting evidence includes similarity to: 1 2C 31 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 103 samples with support for all annotated introns;product=putative uncharacterized protein DDB_G0271606;transcript_id=XM_032929672.1
NC_046178.1     Gnomon  mRNA    8198663 8200917 .       +       .       ID=rna-XM_032929677.1;Parent=gene-LOC116923201;Dbxref=GeneID:116923201,Genbank:XM_032929677.1;Name=XM_032929677.1;gene=LOC116923201;model_evidence=Supporting evidence includes similarity to: 1 2C 20 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 41 samples with support for all annotated introns;product=homeobox protein Hox-B5a-like;transcript_id=XM_032929677.1
NC_046178.1     Gnomon  mRNA    8210283 8219082 .       +       .       ID=rna-XM_032929676.1;Parent=gene-LOC116923200;Dbxref=GeneID:116923200,Genbank:XM_032929676.1;Name=XM_032929676.1;gene=LOC116923200;model_evidence=Supporting evidence includes similarity to: 1 2C 27 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 106 samples with support for all annotated introns;product=homeotic protein Sex combs reduced-like;transcript_id=XM_032929676.1
NC_046178.1     Gnomon  mRNA    8237447 8240876 .       +       .       ID=rna-XM_032929674.1;Parent=gene-LOC116923199;Dbxref=GeneID:116923199,Genbank:XM_032929674.1;Name=XM_032929674.1;gene=LOC116923199;model_evidence=Supporting evidence includes similarity to: 2 2C 25 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 63 samples with support for all annotated introns;product=homeobox protein Hox-A4-like%2C transcript variant X1;transcript_id=XM_032929674.1
NC_046178.1     Gnomon  mRNA    8253193 8275604 .       +       .       ID=rna-XM_032929670.1;Parent=gene-LOC116923194;Dbxref=GeneID:116923194,Genbank:XM_032929670.1;Name=XM_032929670.1;Note=The sequence of the model RefSeq transcript was modified relative to this genomic sequence to represent the inferred CDS: added 1052 bases not found in genome assembly;end_range=8275604,.;exception=annotated by transcript or proteomic data;gene=LOC116923194;inference=similar to RNA sequence (same species):INSD:GDIP01174559.1;model_evidence=Supporting evidence includes similarity to: 1 2C 16 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 32 samples with support for all annotated introns;partial=true;product=uncharacterized LOC116923194;transcript_id=XM_032929670.1
NC_046178.1     Gnomon  mRNA    8288049 8299492 .       +       .       ID=rna-XM_032929671.1;Parent=gene-LOC116923196;Dbxref=GeneID:116923196,Genbank:XM_032929671.1;Name=XM_032929671.1;Note=The sequence of the model RefSeq transcript was modified relative to this genomic sequence to represent the inferred CDS: added 242 bases not found in genome assembly;exception=annotated by transcript or proteomic data;gene=LOC116923196;inference=similar to RNA sequence (same species):INSD:GDIP01019957.1;model_evidence=Supporting evidence includes similarity to: 1 2C 8 Proteins%2C and 99%25 coverage of the annotated genomic feature by RNAseq alignments;partial=true;product=homeotic protein proboscipedia-like;transcript_id=XM_032929671.1
NC_046178.1     Gnomon  mRNA    8316962 8325421 .       +       .       ID=rna-XM_032929673.1;Parent=gene-LOC116923198;Dbxref=GeneID:116923198,Genbank:XM_032929673.1;Name=XM_032929673.1;gene=LOC116923198;model_evidence=Supporting evidence includes similarity to: 1 2C 11 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 113 samples with support for all annotated introns;product=homeobox protein Hox-B1a-like;transcript_id=XM_032929673.1
NC_046177.1     Gnomon  mRNA    2919198 2920876 .       -       .       ID=rna-XM_032927938.1;Parent=gene-LOC116921584;Dbxref=GeneID:116921584,Genbank:XM_032927938.1;Name=XM_032927938.1;gene=LOC116921584;model_evidence=Supporting evidence includes similarity to: 1 EST%2C 11 Proteins%2C and 100%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 108 samples with support for all annotated introns;product=segmentation protein even-skipped-like;transcript_id=XM_032927938.1
```
Once you have instructed <code>grep</code> with the pattern to look for, it will scan your file line by line looking for any occurrence and then print the results to the stdout. Be carefull that the pattern you are looking for is unique, otherwise <code>grep</code> will also... grep unwanted lines.

As we have already seen with [<code>tar</code>](#tar-to-compress-directories-and-man-to-inspect-the-manual-of-a-command), you can change the behaviour of <code>grep</code> by appending many different tags to the main command. If you want to read all the flags that are available for <code>grep</code>, you can look for its manual (*do you remember how to evoke the manual of a UNIX command?*). I'll drop hereafter some of the most-common and useful flags of <code>grep</code> for bioinformaticians:
```bash
#grep the pattern and Count the number of matching lines (N.B.: this flag counts the number of matching lines, not of occurrencies)
$ grep -c "mRNA" example_files/Dmag.HPHG.location.gff
12

#grep the pattern and inVert the search results, i.e., print all the lines that do not match the pattern
$ grep -v "mRNA" example_files/Dmag.HPHG.location.gff
...

#grep the pattern and print also the N lines after each matching, where N is an integer
#here the example allows you to extract the sequence of the ND5 mitochondrial gene of Drosophila
$ grep -A1 "ND5" example_files/Dmel.mito.proteins.faa
>lcl|NC_024511.2_prot_YP_009047273.1_8 [gene=ND5] [locus_tag=Dmel_CG34083] [db_xref=FLYBASE:FBpp0390633] [protein=NADH dehydrogenase subunit 5] [transl_except=(pos:1717..1717,aa:TERM)] [protein_id=YP_009047273.1] [location=complement(6409..8125)] [gbkey=CDS]
MCSISFVNLISMSLSCFLLSLYFLLNDMIYFIEWELVSLNSMSIVMTFLFDWMSLLFMSFVLMISSLVIFYSKEYMMNDNHINRFIMLVLMFVLSMMLLIISPNLISILLGWDGLGLVSYCLVIYFQNIKSYNAGMLTALSNRIGDVALLLSIAWMLNYGSWNYIFYLEIMQNEFEMLMIGSLVMLAAMTKSAQIPFSSWLPAAMAAPTPVSALVHSSTLVTAGVYLLIRFNIILSTSWLGQLMLLLSGLTMFMAGLGANFEFDLKKIIALSTLSQLGLMMSILSMGFLKLAMFHLLTHALFKALLFMCAGAIIHNMNNSQDIRLMGGLSIHMPLTSACFNVSNLALCGMPFLAGFYSKDMILEIVSISNVNMFSFFLYYFSTGLTVSYSFRLVYYSMTGDLNCGSLNMLNDESWIMLRGMMGLLIMSIIGGSMLNWLIFPFPYMICLPIYMKLLTLFVCIVGGLFGYLISLSNLFFLNKSLFMYNLSTFLGSMWFMPYISTYGMIFYPLNYGQLVVKSFDQGWSEYFGGQHLYQKLSMYSKTLFLMHNNSLKIYLLLFVFWILILLILLFL

#grep the pattern and print also the N lines before each matching, where N is an integer
#here the example allows you to know the name and NCBI accession number of a specific protein, knowing its FlyBase identifier
$ grep -B2 "FBpp0100176" example_files/Dmel.mito.genome.gb
                     /product="cytochrome c oxidase subunit I"
                     /protein_id="YP_009047267.1"
                     /db_xref="FLYBASE:FBpp0100176"
```

> Use <code>grep</code> to find a pattern in files and print the matching lines.
>
> Use <code>grep -c</code> to find a pattern in files and print the number of matching lines.
>
> Use <code>grep -v</code> to find a pattern in files and print the non-matching lines.
>
> Use <code>grep -AN</code> to find a pattern in files and print the matching lines plus the following N lines.
>
> Use <code>grep -BN</code> to find a pattern in files and print the matching lines plus the previous N lines.

[↑ Table of contents ↑](#Table-of-contents)

