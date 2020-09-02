## Table of contents ##
1. Basic Linux Commands
2. Enivroment Variables
3. Directories
4. File and Directory Permissions
5. Viewing Filies and The nano editor
6. Editing Files with Vi
7. Various Grapical Editors 
8. Editind Files with Emacs 
9. Delete, Copy, Moving, Renaming, Compress and Creating


## Basic Linux Commands ##

Commands are case sensetive 
**ls** - List directory Contents
**cd** - Changes the current directory 
**pwd** - Displays the present working directory 
**cat** - Concatenates and display Files 
**echo** - Displays arguments to the screem 
**man** - displays the Online Manual 
**exit** - Exist the Shell or your Current session 
**clear** - Clear the screen 
**which** - Locate command
**tac** - displays a file's content in reverse order


Getting help at command line

## Enivroment Variables ##

* storage location Storage location that has a name and a value.
* Typically uppercase
* Access the contents by executing

syntax echo $VAR_NAME

## Directories ##

* Are container for other files and directories 
* Provide a tree like structure 
* Can be accessed by name or shortcut

. => This Directory 
.. => Parent directory
cd - => Change to the previous directory 

**"echo $OLDPWD"** - Hold the directory previously in. 

**mkdir** - create Directory 
**rmdir** - Removes directory/file 
**"rm -rf"** - recursively removes directory and all files inside the folder 

Listing Files and Understanding LS Output

* **"ls -l"** - display the long details of file/directory
* **"ls -a"** - displays the hidden filies inside directory or folder
* **"ls -l -a"** => Can be written as **"ls -la"** or **"ls -al"**
* **"ls -F"** - reveals the file type eg: / - Directory, @ - Link, * - Executable
* **"ls -t"** - List files by time
* **"ls -r"** - Reverse order
* **"ls -latr"** - Long listing including all filies revererse sorted by time
* **"ls -R"** - List files recursively
* **"tree"** - display all files in tree shape 
* **"tree -d"** - display only the filename directories
* **"ls -d <Filename>"** - display the Directory name
* **"ls --color"** - change the color of display 

Symbolic links 
* A link is a points to the actual file or directory 
* use the link as if it were the file 
* **"./<filename>"** - use to run the excutable files
* 

  ## File and Directory Permissions ##

*  When we type **"ls -l"** the first character represnt the file type
   **-** => Regular File
   **d** => Directory
   **l** => Symbolic Link
   eg: 
* Other character represent r for read, w for write and x for Excute
* Permission Catergories 
  u stands for User
  g stands for Group
  o stands for Other
  a stands for All
  permission will be always displayed in order **type-user-group-other**
* Groups
  Ever user is in atleast one group 
  User can belong to many groups

#### Working with group ####

* **"chgrp "** - Command use to change the group of filies
* File creation mask - Dile creation mask determines default permission, If no mask were used permission would be
   777 for directories 
   666 for files 
* **"umask [-S] [mode]"** - Set the file creation mask to mode, If given, Use -S to for  symbolic notation
   [-S] use for symbolic representation
* **cmod** helps in adding or giving permissions, while **umask** turns off, subtracts or takes away permissions
* Common **umask** Mode are 022, 002, 077, 007
* umask 0022 is the same as umask 022
* chmod 0644 is same as chmod 644
* The special modes are 
   i) setuid
  ii) setgid
 iii) sticky
   

  ## Finding Filies and Directories ##

* **"find [path..] [expression]** Recursively finds the diles in path that match expression. if no arguments are supplied it find all filies in the current directory 
find [path] [expression]    //recursively find files in path that match expression

-excec command {} \;        //run command against all the files that are found

find ./temp -iname *t       // '-i' ignore case, '*' matches all with t, 'find' looks for files or directories in temp

* **"Locate"** - is faaster than find command, Quaries an index, Results are not in real time
*  


*  Permisions

ls -l
-rw-rw-r-- 1 akhil users 10400 Sep 27 08:52 sales.data

Symbol      Type
'-'         Regular File
'd'         Directory
'|'         Symbolic Link

'r'         Read
'w'         Write
'x'         Execute

Permission Categories
Symbol      Category
'u'         User
'g'         Group
'o'         Other
'a'         All
'groups' command displays a users groups.

Linux Directories

Changing Permissions
chmod       - Change mode command
ugoa        - User category user, group, other, all
+-=         - Add, substarct, or set permissions
rwx         - Read, write, Execute
eg

chmod a=r sales.data
chmod u=rwx, g=rx sales.data


 ## Viewing Filies and The nano editor ##

#### Displaying the Content of Filies ####
 
 ```
 **"cat <filename>"** - Display the contents of File 
 **"more <filename>"** - Browse through text file 
 **"less <filename>"** - More feature than more 
 **"head <filename>"** - Output the begining (or top) portion of file, ie first lines of file.
 **"tail <filename>"** - Output the ending (or bottom) portion of file, ie last line of file.
 **"tail -f <filename>"** - follow the file, Displays data as it is beign written to file

 ``` 
 *Note* 
 head and tail - Displays only 10 lines by default 
                 change in behaviour with -n, where n = number of lines, 
                 eg: tail 15 file.txt
 
#### Nano editor ####

 * Nano is a siple editor. Easy to learn. Note advanced as vi or emacs.
 * If nano isnt available, look for pico
 ```
 ctrl + x - to exit the file
 ctrl + o - to save the file
 ctrl + g - to get help about nona
 ```                          

 ## Editing Files with Vi ##

#### Vi Editor ####

* Has advanced and powerfull feature, Not intuitive  
* Requies a time investment 
  ```
  **"vi <Filename>"** - Edit file 
  **"vim <Filename>"** - Same as vi, but more features
  **"view <Filename>"** - Starts vim in read-only mode
  ```
* Vi always works in three mode  
   i) command Mode - Allows to navigate about the file, perform searches, copy text, delete text and paste text
  ii) insert mode - 
 iii) line mode  - Is used to navivagest between the lines in the file
 *Note*
  *To navigate to command mode in Vi press **Esc** key.
* Vi mode and shortcuts
  ```
  1. Vi Command Mode and Navigation 
     * k - Up one line
     * j - Down one line 
     * h - Left one character 
     * l - Right one character 
     * w - Right one word 
     * b - left one word
     * ^ - Go to the begining of the line
     * $ - Go to the end of the life
     * below images shows how k,j,h,l works
     * ![Linux Directories](/linux-directories.png?raw=true "Title")  
  2. Vi insert mode
     * i - Insert at the cursor postion 
     * I - Insert at the begining of the line
     * a - Append after cursor position
     * A - Append at the end of the line
  3. Vi Line mode
     * :W - writes(saves) the file
     * :W! - Forces the file to be saved
     * :q - Quit
     * :q! - Quit without saving chnages
     * :Wq! - write and quit
     * :x - same as :wq   
     * :n - Positions the currsoe at line n.
     * :$ - Positions the cursor on the last line
     * :set nu - Turn on line numbering
     * :set nonu - Turn off line numbering
     * :help - get help
  ```
  #### Vi - Repeating Commands ####
* Repeat a command by preceding it with a number 
   * 5k = Move up a line 5 times
   * 80i<text><ESC> = Insert<text> 80 times
   * 80i_<Esc> = Insert 80 "-" characcters

 * Vi Commands 
  ```
  * x - Delete a character
  * dw - Delete a  word
  * dd -Delete a line
  * D - Delete from current position
  * r - Replace te current character 
  * cw - Change the current word
  * cc - Change the current line
  * c$ - Change the text from the current position
  * C - Same as c$
  * ~ - Reverse the case of a character
  * yy - Yank(copy) the current line
  * y<psoition> - Yanl the <position>
  * p - Paste the most recent deleted or yanked text
  * u - Undo
  * ctrl-R - redo
  * /<pattern> - Start a forward search
  * ?<pattern> - start a reverse search
  ```

 ## Editind Files with Emacs ##
 
* Powerfull edit as vi. we can use either vi or Emacs
* ```
  syntax  **"emacs <filename>"**
  
  *Note*
  C-<char>  - C stands for ctrl
  M-<char>  - M stands for alt key
  M-<char>  - M stands for Esc key also
  ``` 
* Emacs commands
  ```
  C-h         - Help
  C-x C-c     - Exit
  C-x C-s     - Save the file
  C-h t       - Built-in tutorial
  C-h k <key> - Describe key, get help on specfic key command
  C-p 	      - Previous line 
  C-n         - next line
  C-b         - Backward one character 
  C-f         - Forward one character
  M-f         - Forward one word
  M-b         - Backward one word
      Navigation Commands
  C-a         - Go to the beginin of the line
  C-e         - Go to the end of the line
  M-<         - Go to the begining of the line
  M->         - Go to end of the line
       Deleting Commands
  C-d         - Delete a character
  M-d         - Delete a word
       copy,paste
  C-k         - Cut(Kill)
  C-y         - Paste
  C-x u       - Undo
       other commands
  C-s         - Start a forward search
  C-r         - Start a reverse search
  C-u N <coomand> - Repeat <command> N times
  C-x c       - to exit 
  C-h t       - Built-in tutorial
  ``` 

 ## Various Grapical Editors ##

* Few graphical editors are 
   * emacs - Emacs has a graphical mode too
   * gedit - The default text editor for Gnome, similar to Notepad
   * gvvim - The graphical version of vim
   * kedit - The default text editor for the KDE.
   * Abiword - Same as Microsoft word alternative
   * LibreOffice - Full office suite
   * kate - source code editor

 ## Delete, Copy, Moving, Renaming, Compress and Creating ##

 #### Delete Filies ####  
 ```
  "rm <filename>"     - Remove file
  "rm -r dir"         - Remove the directory and its content recursively
  "rm -f <filename>"  - Force removal and never prompt for conformation
 ```

 #### moving and renaming Files ####  
 ```
  "mv"                         - move or rename files and directories      
  "mv source destination"      - move from soucre to destination 
  "mv source"                  - the source file will be renamed
  "mv -i source destination"   - to overwrite the destination
 ```

 #### Sort data ####  
 ```
  "sort file"  - sort text in file.
  " -k F"      - Sort by key. F is field number.
  " -r "       - Sort in reverse order.
  " -u "       - Sort in uniquie.
 ```

 #### Create collection of files ####  
 ```
  "tar [-] c|x|t f tarfile [pattern]"  - Crate, extract or list contents of a tar archivve using pattern, if supplied.
  c      - Create a tar archive
  x      - Extract files from the archive
  t      - Display the table of contents (list)
  v      - Be verbose
  z      - Use compression
  f file - Use this file
 ```

 #### Disk uasage ####  
 ```
  du     - Estimates file usage
  du -k  - Display sizes in Kilobytes
  du -h  - Displays sizes in human readable format
 ```
