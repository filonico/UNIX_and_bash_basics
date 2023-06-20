# UNIX and Bash basics for trainee students
This repository is meant to introduce trainee students of the EVO•COM group of the University of Bologna to the Bash environment and as a general reference to retrieve most common commands used in bioinformatics.

**Enjoy!**

## Table of contents
  - **[Command cheat sheet](#command-cheat-sheet)**
  - **[UNIX, Linux and Bash: let's make things clear](#unix-linux-and-bash-lets-make-things-clear)**
    - [UNIX is a family of operating systems](#unix-is-a-family-of-operating-systems)
    - [GNU/Linux is a UNIX-like operating system](#gnulinux-is-a-unix-like-operating-system)
    - [The shell is a command-line interpreter](#the-shell-is-a-command-line-interpreter)
    - [Bash is a UNIX shell and a command language](#bash-is-a-unix-shell-and-a-command-language)
  - **[Login to a remote machine (ssh)](#login-to-a-remote-machine-or-server)**
  - **[Basic commands to manage directories and files](#basic-commands-to-manage-directories-and-files)**
    - [<code>pwd</code>, <code>cd</code> and <code>mkdir</code> to manage directories](#pwd-cd-and-mkdir-to-manage-directories)
    - [<code>cat</code>, <code>less</code>, <code>head</code> and <code>tail</code> to read file content](#cat-less-head-and-tail-to-read-file-content)
    - [<code>cp</code> and <code>mv</code> to copy/paste and cut/paste files](#cp-and-mv-to-copypaste-and-cutpaste-files)
    - [<code>gzip</code>/<code>gunzip</code> and <code>zip</code>/<code>unzip</code> to work with compressed files](#gzipgunzip-and-zipunzip-to-work-with-compressed-files)
    - [ <code>tar</code> to compress directories and <code>man</code> to inspect the manual of a command](#tar-to-compress-directories-and-man-to-inspect-the-manual-of-a-command)
  - **[Bash scripting](#bash-scripting)**
  - **Find in a file, find and replace and working with "tables" (grep, sed, awk)**
  - **Working with conda environments**
  - **Working in screen sessions**
  - **Working with git (git clone, git push, git pull, git add,...)**

## Command cheat sheet
| Command | Meaning | Description |
| --- | --- | --- |
| [<code>man</code>](#tar-to-compress-directories-and-man-to-inspect-the-manual-of-a-command) | *manual* | Print the manual of a UNIX command|
| [<code>ssh</code>](#login-to-a-remote-machine-or-server) | *secure shell* | Log-in to remote machines |
| [<code>pwd</code>](#pwd-cd-and-mkdir-to-manage-directories) | *print working directory* | Print the full path of the directory you are in |
| [<code>cd</code>](#pwd-cd-and-mkdir-to-manage-directories) | *change directory* | Change your working directory |
| [<code>mkdir</code>](#pwd-cd-and-mkdir-to-manage-directories) | *make directory* | Create a new directory|
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
| [<code>tar</code>](#tar-to-compress-directories-and-man-to-inspect-the-manual-of-a-command) | *tape archive* | Create an archive of a directory (and compress it if desidered) |

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
Many UNIX shells exhist nowadays, but the most popular is the <ins>B</ins>ourne-<ins>A</ins>gain <ins>Sh</ins>ell (**Bash**), a replacement of the original Bourne shell (sh). Bash is essentially a command and programming language and, as such, it uses its own syntax and grammar. So, be aware that the same command may not work in the same way between different shells (even between UNIX shells). Bash, for example, uses a dollar symbol (**<code>$</code>**) as its own prompt, that is, when the shell is ready to receive a command it will display a <code>$</code> (not by chance, the <code>$</code> is also present in the bash logo) . On the contrary, a C shell will display a <code>%</code> as a prompt.

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
which stands for *<ins>p</ins>rint <ins>w</ins>orking <ins>d</ins>irectory*. Usually, when opening the shell, you enter by default your <code>home</code> directory, which is shortened by the symbol <code>~</code>.

If you want to change your working directory and navigate thourgh the directories, for example to reach the desktop of your local machine, just type:

```bash
$ cd /path/to/your/Desktop/
```
where <code>cd</code> stands for *<ins>c</ins>hange <ins>d</ins>irectory*. Some other useful <code>cd</code> commands are:

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
where <code>mkdir</code> stands for *<ins>m</ins>a<ins>k</ins>e <ins>dir</ins>ectory*.

> Use <code>pwd</code> to print the absolute path of the working directory.
> 
> Use <code>cd</code> to move to a different directory.
> 
> Use <code>mkdir</code> to create a new directory.

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
where <code>cp</code> stands obviously for *<ins>c</ins>o<ins>p</ins>y*.
  
However, the storage memory is not limitless, so sometimes it is more convenient to **cut** your files and **paste** them in a different location on your storage, by usig:
```bash
#move a file to a different location and keep the original name
$ mv your_file.txt new/location/of/your_file.txt
#move a file to a different location and rename it
$ mv your_file.txt new/location/of/your_file_new.txt
# if you do not specifiy a different directory, the file will be just renamed
$ mv your_file.txt your_file_new.txt
```
where <code>mv</code> stands for *<ins>m</ins>o<ins>v</ins>e*.
  
> Use <code>cp</code> to copy and paste files.
> 
> Use <code>mv</code> to cut and paste files or to rename them in their current directory.

[↑ Table of contents ↑](#Table-of-contents)

## <code>gzip</code>/<code>gunzip</code> and <code>zip</code>/<code>unzip</code> to work with compressed files

As we have already pointed out, bioinformatic files are often very big in size (sometimes dozens of gigabytes) while our storage capacities are often (much) more restricted. Large files are also difficult to handle when being transferred to collegues via email or other protocols. Thus, it is foundamental that you carefully store your files in a way that allows you to save as much bytes as possible.

To this purpose, you can easily **compress your files** by using <code>gzip</code>, a <ins>zip</ins>ping program which was originally intended for <ins>G</ins>NU users. With <code>gzip</code> you can also choose the compression ratio by specifying a number between <code>1</code> (low compression ratio) and <code>9</code> (high compression ratio; default is <code>6</code>):
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

## <code>tar</code> to compress directories and <code>man</code> to inspect the manual of a command
We have just seen how we can save space up by compressing single files. But what about compressing an entire directory? What if you want to archive your recent research (now published on *Nature*) on the gene-family dynamics in hematophagous dipterans? Unfortunately, <code>gzip</code> and <code>zip</code> can basically manage only single files, so you have to rely on other utilities.

<code>tar</code> is a command that allows you to **organize a whole directory** into a single *<ins>t</ins>ape <ins>ar</ins>chive*, which can be subsequently compressed. <code>tar</code> can archive and compress a whole directory all in the same command line and you just need to specify the name of the output compressed archive and the input directory:
```bash
#archive and compress our example_files/ directory
$ tar -c -v -z -f example_files.tar.gz example_file/
#or, in short
$ tar -cvzf example_files.tar.gz example_file/
```
where <code>-c</code> instructs the command to *<ins>c</ins>reate* a new archive, <code>-v</code> instructs to be *<ins>v</ins>erbose* on the stdout, <code>-z</code> instructs to *g<ins>z</ins>ip* the archive, and <code>-f</code> specifies the output *<ins>f</ins>ile* name.

Here you have just been introduced to **flags** (<code>-c</code>, <code>-v</code>, <code>-f</code>, etc., are all flags of <code>tar</code>), i.e., options that can be passed to the main program to modify its behaviour. Just by changing the various accepted flags, <code>tar</code> can accomplish different tasks. For example, you can use <code>tar</code> also to **un-compress and un-archive** a directory:
```bash
#archive and compress our example_files/ directory
$ tar -v -x -f example_files.tar.gz
#or, in short
$ tar -vxf example_files.tar.gz
```
where <code>-x</code> instructs the command to *e<ins>x</ins>tract* (uncompress) the gzip archive.
To know all the flags available for a certain UNIX tool, you can rely on the <code>man</code> command, which will print to the stdout the *<ins>man</ins>ual* of your interest:
```bash
#print the manual of tar
$ man tar
```

>Use <code>tar -cvzf</code> to compress a whole directory
>
>Use <code>tar -xzf</code> to uncompress a gzip directory
>
>Usa <code>man</code> to inspect the manual of a UNIX command

[↑ Table of contents ↑](#Table-of-contents)

# Bash scripting

|, >, &&, ||, variables, for cycle, if statements, while cycle,...

[↑ Table of contents ↑](#Table-of-contents)
