# Practice Terminal

## Introduction

Bash command line interface, `Terminal`, is an interface to do some commands  without Graphical User Interface (GUI).  

Actually, The GUI is much easier but the reason to use terminal is that some operations are much suited in Terminal. In addition, some developer will work with him could prefer using a terminal.  

### The Command Line  

---

To open the terminal in Ubuntu we can using **Alt+Ctrl+T**  

To know what shell we are using we can type in terminal:  

> - **`renad@renad-HP-Notebook:~$`** echo $SHELL  

- **The command stored in Terminal and we Can reach them using up and down arrows**  

### Basic Navigation

---

1. To know where we are (path), we can use Print Working Directory (pwd):

>- **`renad@renad-HP-Notebook:~$`**  pwd  

2. To show the list of folders and files in the place where we current are, we can use list (ls)

>- **`renad@renad-HP-Notebook:~$`** ls  

3. To change the directory we are in, we have to use change directory command (cd). Adding a path after cd is optional using `/` or just write the next directory. the directory have to be in the place we are in or we got an error.  

>- **`renad@renad-HP-Notebook:~$`** cd directoryName
>
>- **`renad@renad-HP-Notebook:~$`** cd Path

We can also use dot to go inside directory or double dot to go out the directory

>- **`renad@renad-HP-Notebook:~$`** cd ./directoryName => *Go through this directory*
>
>- **`renad@renad-HP-Notebook:~$`** cd ./Path  => *Go Through this Path*
>
>- **`renad@renad-HP-Notebook:~$`** cd ../ => *Go back outside one step*

**The Path either relative which relative to where we currently are in the file system or Absolute that relation to the file system.**  

#### Some important places  

`a.` **cd /etc** : to show all config file of our system.  
`b.` **cd /var/log**: Stores log files for various system programs.  
`c.` **cd /bin** or **cd /usr/bin**: Show the several used programs
The location of several commonly used programs.  
`e.` **cd** : if we use cd without anything it will jump to the root.

### More About File

---

Everything in ubuntu is a file: the text,execution or image if a file regarding to Linux. Meanwhile is Extensionless System which means That Ubuntu looks inside the file to determine what type of file it is.

If the image extension is changed to text for example to another the Ubuntu system still see the file as image.  

**Linux System is case sensitive.**  

**If the folder name had 2 part or more separate using space we need to use Quote or using Escape (`/`) to remove the space.**  

>- **`renad@renad-HP-Notebook:~$`** cd "Practice Terminal"  
**OR**
>- **`renad@renad-HP-Notebook:~$`** cd Practice\ Terminal  

To show the hidden file, User should use -a after cd

>- **`renad@renad-HP-Notebook:~$`** cd -a Desktop  

### Manual Pages

 ---
 we can find what the command do and some description using manual page (man).  

 >- **`renad@renad-HP-Notebook:~$`** man ls

 Please Look at this specific example section [man Example](https://ryanstutorials.net/linuxtutorial/manual.php#:~:text=to%20look%20up%3E-,man%20ls,-Name) to see the result of the command.

### More on the Running of Commands

---
To get all directories:  

>- **`renad@renad-HP-Notebook:~$`** ls -a
>
>- **`renad@renad-HP-Notebook:~$`** ls --all

### File Manipulation

---

`a.` To make Directory:  

>- **`renad@renad-HP-Notebook:~$`** mkdir directoryName.  

`b.` To remove Directory:  

>- **`renad@renad-HP-Notebook:~$`** rmdir directoryName.  

`c.` To create a file:  

>- **`renad@renad-HP-Notebook:~$`** touch fileName.  

`d.` To copy file or Directory:  

>- **`renad@renad-HP-Notebook:~$`** cp fileOrDirectoryName **< source >** **< Destination >**  

- we can use the path instead of source or destination.  

`e.` To copy file or Directory:  

>- **`renad@renad-HP-Notebook:~$`** mv fileOrDirectoryName **< source >** **< Destination >**  

- we can use mv to rename the file or directory.  

`f.` To remove file or **NOT** empty Directory:  

- *To remove a file:*

>- **`renad@renad-HP-Notebook:~$`** rm fileName  

- *To remove non Directory using **-r***

>- **`renad@renad-HP-Notebook:~$`** rm -r DirectoryName  

### Cheat Sheet

---
A quick reference for the main commands covered in this tutorial [Linux Tutorial - Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)  

Resource: [Bash Command Line Tutorials](https://ryanstutorials.net/linuxtutorial/).
