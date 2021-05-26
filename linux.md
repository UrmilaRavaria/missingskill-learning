# Linux 
* Is a kernel
* Also known as GNU/Linux : `GNU` - Operating system and `Linux` - kernel.
* License : GPL (General Public License)
* Multi user system each have their own home.
* don't need extension like .txt, .exe etc. `Everything is a file or directory`. 
## **History**
In 1991 `Linus Torvalds` created linux kernel.
`Richard Stallman` started to building GNU operating system in 1983. After 1985 started Free software Fountation. 
<br>
<br>

## **Popular Linux Distro**
* Debian
   * Ubuntu
      * Mint
   * Kali
* Redhat
   * Fedora
   * CentOS
* Android
<br>

*nix - all distrubation inspired from Unix. Which include Linux, FreeBSD etc.

## **Commands** 
<br>

### **pwd** : present/print working directory, gives absolute path. To check which directory you are in.
### **man**: display manual page for given command.
* man <command_name>

## Commands to create files and directory.
### 1. **mkdir** : used to create a directory in current directory.
* mkdir <dir_name>

   ### Flags
  * mkdir -p <user/download/pic> : creates parent directory as needed. will create user dir with download dir which has pic directory.
### 2. **touch** : create a file
* touch <file_name>


### **ls** : list information of directory and files of current directory by default.
 ### Flags
  * ls -a : list all the file and dir also the hidden files.
  * ls -h : shows file size in human readable format.
  * ls -r : prints list in reverse order.
  * ls -l : prints list in more detail. 
  * ls -F : classify when dir auto add / at end of file name.
  * ls -t : shows w.r.t modification time.
  *  ls -R : recursively prints all the directory contents as well.

## Command to navigate files and through files across file system.
### 1. **cd** : to change a directory
* cd : takes you to home directory.
* cd .. : takes one step back in directory tree.
* cd - : to toggle between directorys.
* cd / : takes to root directory.
* cd ~ : takes to users home directory.
### 2 .**mv** :  to move files also used to rename a file.
* mv <file_name> <dir_name_OR_path_to_dir>
* mv <old_file_name> <new_file_name>
### 3 .**cp** : copys given file to given distation.
* cp <file_name_OR_path_of_file> <path_to_destination>

  ### Flags
   * cp -R <source_dir> <destination_dir> : recursively copy content of source directory to destination directory.

## Commands to display file content
### 1. **cat** : concatenate file
* cat <file_name> : display the content of file specified.
* cat fist_file > second_file : will overrite the second_file with content of fist_file.
* cat fist_file >> second_file : will append the content of fist_file to content of second_file.
* cat < first_file : will output the content of first_file.
### 2. **tail** : prints last few lines 10 by default.
* tail <file_name>
   ### Flags 
   * tail -n <no_of_line> <file_name> :
will display specified number of line from specified file.
   * tail -f <file_name> : follow/ watch continously the specified file.
### 3. **more** : load entire file in memory and then display it.
* more <file_name>
### 4 .**less** : Display content of file page by page.Load file part by part therefor faster then more command.
* less <file_name>

## Commands to remove files.
### 1. **rm** : remove file 
* rm <file_name> : delete file specified.
### Flags
* rm -r <dir_name> : recursively deletes files and directory
* rm -f <file_name> : remove file forcebly.
### 2. **rmdir** : remove dir if it is empty
* rmdir <dir_name>


### **which** : locate executable file of command that is given as argument.
* which <command_name> : will display location of executable file og given command.
### **who** : display username of all current logged in user in machine.
### **whoami** : display username of current logged in user in shell.
### **echo** : prints to the terminal or file.
* echo <"String you want to print">
### **ps** : non-interactive, display currently running processes.
### **top** : interactively/continuosly display process information cpu and memory utalization.
### **ping** : to check connection to given server.
* ping <host_name_OR_IP-addr>
### **ifconfig** : display network configuration

### **wget** : command line browser.
* wget <URL>
### **apt-get** :  used to install packages.
* apt-get install <pakage_name>
### **clear** : clears the terminal.
### **exit** : exits the terminal.
### **history** : shows history of aommands used.

## **Wildcard in Linux**

symbols that stands for character.
* asterisk `*` – represent no or more accurrence of any character. 
eg : `ls a*d` : will list all files in current directory that start with a and ends with d. there can be any number of character in between a and d. Like addd, add, ad but not addg.
* mark `?` – represent/match single occurrence of any character.
i.e `ls a??d` : will list all file in current directory that start with a and ends with d and has exactly two character in between them. Like addd,aimd but not addrd,add .
* brackete `[ ]` – matches the characters enclosed inside it they can be any character number, letter etc.
eg : `ls a[de]d` : will list all files in current directory that start with a and ends with d and have either d or e in between them. Like add,aed but not aded.


<br>
<br>

## **File System**

| File | Description |
|-------|-------------|
|/bin  | binary files (commands are stored here).|
|/dev | device file for devices |
|/home | user are created here.|
|/lib |  shared librarys used by system are stored here.|
|/mnt | mount point for filesystems |
|/proc | virtual file system when application starts stores the system configuration.|
|/sys | virtual file system stores and modifies information about device.|
|/usr | user system directory.|
|/boot | kernel is stored here, also includes files need for boot process.|
|/etc | configeration file are here, user binary,libaries are stored here.|
|/media | mount point for removable media.| 
|/opt | third part application and software.|
|/root | home directory of root user, Used by system admin.When you are in this directory insted of `$` `#` is displayed indicating root|
|/sbin | system binary, used by system admin.|
|/tmp | temporary files |
|/var | variable files (log files)|

