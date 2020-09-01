 Linux 
The Complete Linux Course: Beginner to Power User!

 ## Common Directories ## 
 
1. **/Root** - Highest in hireachy
2. **/bin** - binaries and other executable programs
3. **/etc** - System configuration file 
4. **/home** - home directories
5. **/opt** - optional or thrid party software 
6. **/tmp** - tempory space, typicall cleared on reboot
7. **/usr** - user related programs 
8. **/var** - variable most notable log files
All the above directories can have sub folder/directires inside it

## Shell ##

Shell - A program that accepts your commands and executes the commands.
Shell is the default UI of a linux sysytem.
Terminal gives acces to the shell.
Command line is more powerfull

### root ###

Root is systems superuser
Normal accounts can only do a subset of the things root can do.
Root access is typically restricted to sysytema administrators.
 
## Basic Linux Commands ##

Commands are case sensetive 
* **ls** - List directory Contents
   i) **"ls -l"** -- gives the list  of files with created date 
  ii) **"ls -r"** -- gives the folder name in reverse order 
 iii) **"ls -p"** --  append / indicator to directories
* **cd** - Changes the current directory 
   i) **"cd ./<filename>"** -- use to specfic an absolute path 
   ii) **"cd ../"** -- use to go to parent folder 
  iii) **"cd ~"** -- use to go to Home
* **pwd** - Displays the present working directory 
* **cat** - Concatenates and display Files 
* **echo** - Displays arguments to the screem 
* **man** - displays the Online Manual 
* **exit** - Exist the Shell or your Current session 
* **clear** - Clear the screen 
* **which** - Locate command
* **tac** - displays a file's content in reverse order


 ## Administrative privileges in terminal ##
 
1. when we try to edit permission denied files we cannot edit file directly for such cases we use command "**"sudo nano ./<filename>"**
2. **sudo !!** -- is use to run the pervious sudo commands
3. **sudo su** -- is use to change the user of computer it becomes rootuser you can edit all the files
 
  ## Enivroment Variables ##

* storage location Storage location that has a name and a value.
* Typically uppercase
* Access the contents by executing

syntax echo $VAR_NAME

  ## Directories ##

* Are container for other files and directories 
* Provide a tree like structure 
* Can be accessed by name or shortcut

* **.** => This Directory 
* **..** => Parent directory
* **"cd -"** => Change to the previous directory 
* **"echo $OLDPWD"** - Hold the directory previously in. 
* **mkdir** - create Directory 
* **rmdir** - Removes directory/file 
* **"rm -rf"** - recursively removes directory and all files inside the folder 

  ## Listing Files and Understanding LS Output ##

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
 
   #### Symbolic links #### 
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
* **cmod** helps in adding or giving permissions, while **umask** turns off, subtracts or takes away permissions
* Common **umask** Mode are 022, 002, 077, 007
* umask 0022 is the same as umask 022
* chmod 0644 is same as chmod 644
* The special modes are 
   i) setuid
  ii) setgid
 iii) sticky
 
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
  vi <Filename> - Edit file 
  vim <Filename> - Same as vi, but more features
  view <Filename> - Starts vim in read-only mode
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
      k - Up one line
      j - Down one line 
      h - Left one character 
      l - Right one character 
      w - Right one word 
      b - left one word
      ^ - Go to the begining of the line
      $ - Go to the end of the life
  2. Vi insert mode
      i - Insert at the cursor postion 
      I - Insert at the begining of the line
      a - Append after cursor position
      A - Append at the end of the line
  3. Vi Line mode
      :W - writes(saves) the file
      :W! - Forces the file to be saved
      :q - Quit
      :q! - Quit without saving chnages
      :Wq! - write and quit
      :x - same as :wq   
      :n - Positions the currsoe at line n.
      :$ - Positions the cursor on the last line
      :set nu - Turn on line numbering
      :set nonu - Turn off line numbering
      :help - get help
  ```
  #### Vi - Repeating Commands ####
 * Repeat a command by preceding it with a number 
   * 5k = Move up a line 5 times
   * 80i<text><ESC> = Insert<text> 80 times
   * 80i_<Esc> = Insert 80 "-" characcters

 * Vi Commands 
  ```
   x - Delete a character
   dw - Delete a  word
   dd -Delete a line
   D - Delete from current position
   r - Replace te current character 
   cw - Change the current word
   cc - Change the current line
   c$ - Change the text from the current position
   C - Same as c$
   ~ - Reverse the case of a character
   yy - Yank(copy) the current line
   y<psoition> - Yanl the <position>
   p - Paste the most recent deleted or yanked text
   u - Undo
   ctrl-R - redo
   /<pattern> - Start a forward search
   ?<pattern> - start a reverse search
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

 ## Wildcards ##
 
 * A Character or string used for matching file or directories name
 * Globbing expands the wildcard pattern into a list of files and/or directories.
 * Wildcards can be used with most commands
     * ls 
     * rm
     * cp
 * Commands 
   ```
    *    - Matches zero or more characters
           eg: *.txt, a*, a*.txt
    ?    - Matches exactly one character 
           eg: ?.txt, a?, a?.txt 
   []    - A character class, Matches any of the characters included between the brackets. Matches exactly one character
           eg: [aeiou], ca[nt]
    ```
    ```
   "[!]"    - Matches any of the characters Not included between the brackets. Matches exactly one character
               eg: [!aeiou] reult such as baseball,cricket
   [a-g]  - Matches all files that start with a,b,c,d,e,f or g
   [3-6]  - Matches all files that start with 3,4,5 or 6
   \     - Escape character use if you want to match a wildcard character
   Predefined Characters
   [[:alpha:]]   - Matches all the character alphabets include lower cas and uppercase
   [[:alnum:]]   - Matches alphanumber characters(alhabets & digit)
   [[:digit:]]   - Matches numeric value
   [[:lower:]]   - Matches all the lower case aplhabets
   [[:space:]]   - Matches white space,tab,new lin characters
   [[:upper:]]   - Matches all the upper case alphabets
    ``` 
    
 ## Input, Output and Redirection ##

 * There are mainly three types of I/O
     i) Standard Input - Abbr => stdin, file deescriptor- 0
    ii) Standard Output - Abbr => stdout, file deescriptor- 1 
   iii) Standard Error - Abbr => stderr, file deescriptor- 2
    File descripto - are just number to open file 

   * Redirection
```
    >      redirects output from a command to a file 
   >>      redirects standart output to a file 
    <      redirects input file to a command
   &       Used with redirection to signal that a file descriptor is being used
   2>&l    Combine stderr and standard output
  "2>file"   Redirect standard error to a file
  "null"    Redirect output to nowhere
```

 ## Comparing Files ##

 * Commands 
 ```
 diff file1 file2     - Compare two files
 sdiff file1 file2    - Side by side comparison
 vimdiff file1 file2  - Highlight difference in vim
    Vimdiff 
 ctrl -w w  - Go to next window
 :q         - Quit(close current window)
 :qa        - Quit all (close both files)
 :qa!       - Force quit all
 ```
   ## Searching in Files and using pipes ##
 ```
 grep - To look for text within a file, Display lines matching a pattern
        Syntax - **"grep <particular pattern we are searching for> <Filename>"**
        eg: grep user secret
 -i   - Perform a search, ignoring case
        eg: grep -i User secret
 -c   - Count the number of occurences in a file.
        eg: grep -ci User secret
 -n   - preced ouput with line number.
        eg: grep -ni User secret
 -v   - Invert match. Print lines that dont match
        eg: grep -vi User secret
 ```
 
  #### Pipe ####

 * pipe '|' chains two commands.
 * Takes the standard output from the preceding command and passes it as the standard input to the following command.
 * Error messgaes from the first command will not be passed to second command by default.
 ```
 Syntax => cat file | grep pattern
 ```
 #### cut command #####
 ```
 Syntax => cut [file]          //Cut out selected portions of file. If file is omitted, use standard input.
 ```
 #### Cut options #####

 * -d delimeter Use delimeter as filed seperator.
 * -f N Display the Nth field

 ## Transfering and Copying files over the network ##

 #### Copying Filies over the Network ####

 * To copy files from llocal work station to a linux server or between linux servers we need to use 'SCP' or 'SFTP'.
 * Two Types 
     * SCP - Secure Copy
     * SFTP - SSH file transfer Protocol/Secure file transfer protocol. When use local files and remote files use SFTP.
 * To copy files from llocal work station to a linux server or between linux servers we need to use 'SCP' or 'SFTP'.

 #### Graphical SCP/SFTP Clients ####
 * Cyberduck
 * FileZilla
 * WinSCP
 
 #### File transfer ####
 * SCP 
   ```
   Syntax : **"scp <filename> <destination>"**
   eg: scp z.txt linxsvr:/home/Desktop
   ```
 * SFTP 
   ```
   syntax : **"sftp <hostname>"** - start a file transfer session with host.
            use **"put <filename>"** - to transfer the file
   eg: sftp linuxsvr 
       put z.txt => z.txt file will be aviable in remote
   ```
 * FTP 
   ```
   syntax : **"ftp <hostname>"** - start a file transfer session with host.
            use **"put <filename>"** - to transfer the file 
   eg: ftp linuxsvr 
       put z.txt => z.txt file will be aviable in remote
   ```

 ## Customize the Shell Prompt ##
 
 * Use an Environment variable to customize 
 * For Bash, ksh and sh use enviroment variable "PS1" is used to set the primary prompt string
 * For Csh, tcsh and zsh use enviroment variable "prompt"
 #### Customizing prompt with PS1 ####
 ```
 \d - Date in "Weekday Month Date" format "Tue May 26"
 \h - Hostname up to the first period
 \H - Hostname
 \n - Newline
 \t - Current time in 24-hour HH:MM:SS format
 \T - Current time in 12-hour HH:MM:SS format
 \@ - Current time in 12-hour am/pm format
 \A - Current time in 24-hour format
 \u - Username of the current user
 \w - Current working direectory
 \W - Basename of the current working directory
 \$ - If the effective UID is 0, a #, otherwise a $
 ```
             
 ## Shell Alises ##

 * If we want to type the same command over and over again we can create shortcut called an alias.
 * An alias can be thought of as a text expander 
 * Alias comes predefined in many linux commands
 * Syntax 
   ```
    Syntax - **"alias [name[=value]]"**

   ```
 * commands
   ```
    $ alias grpe='grep' -  Fix Typos 
    $ alias cls='clear' - Make Linux behave like another OS 
         Removing Aliases 
    unalias name - Remove the name alisas
    unalias -a - Remoove all Aliases
   ```

 ## Enviroment Variables ##
 
 * An environment variable is a storage location that has a name and a value.They often affect the way programs behave
   eg: EDITOR=nano
 * ```
    syntax   : **"printenv <enviroment variable name>"**
    syntax 2 : **" echo $<enviroment variable name>"**
   ```
 * Environment variables are upper case by convection, rarely we see lowercase 
 * Creating and removing an Enviroment variable 
   ```
       Creating
   Syntax  : **"export VAR="value""**
             eg: export EDITOR="vi"
       Removing
   Syntax : **"unset VAR"** 
   ```
 
  ## Processes and Job control ##

  ```
    ps              - Display process status
    ps -e           - Display all process
    ps -f           - Full format lisitin
    ps -p pid       - Display usernames processes
    ps -e --forest  - Display a process tree
    ps -u username  - Display user's processes. 
    ps -ef          - Display all process 
    ps -eH          - Display process tree 
        Other  ways to view process
    pstree    - Display processes in a tree format
    top       - Interactive process viewer
    htop      - Interactie process viewer
  ``` 

  #### Background and foreground process ####

  ```
  command &    - Start command in background
  ctrl-c       - Kill the foreground process
  ctrl-z       - Suspend the foreground process
  bg [%num]    - Background a suspened process
  fg [%num]    - Foreground a background process
  kill [%num]  - Kill a process by job number or PID
  jobs [%num]  - List Jobs 
  kill 123     - Kill by process ID
  ```
  ## Switching user ##

 * Commands
 ```
 su [username]   - Change user ID or becomsuperuser
 su -            - A hypen is used to provide enviroment similar to what the user would expect had the user logged in directtly
 su -c ommand    - Specify a command to be excuted, if command is more than one lenght it should be given in quotes
 whoami          - Returns your current account name
      Sudo commands
 sudo -l         - List available commands
 sudo command    - Run command as root
 sudo -u user command    - same as above
 sudo -u root command    - Run as user
    Change the sudo configuration
 visudo                  - Edit the /etc/sudoers file
 ```

 ## Shell Histroy ##
 
 * Executed commands are added to the history  
 * Shell history can be displayed and recalled 
 * Shell history is stored in memory and on disk 
    * ~/.bash_history
    * ~/history
    * ~/.histfile
 * By defualt shell history saves 500 commands in history
 *  Commands 
  ```
   history    - Displays the shell history
   HISTSIZE   - Controlss the number of commands to retain in history
                eg: export HISTSIZE = 1000
   !N         - Repeat command Line number N
   !!         - Repeat the pervious command lline 
   !string    - Repeat the most recent command starting with "string"
   !^         - Represents the first argument ie !:1
   !$         - Represents the last argument
       Searching Shell history 
   ctrl-r     - Reverse shell history search
   Enter      - Excute the  command
   Arrows     - Change the command
   ctrl-g     - Cancel the search
   
  ```
 * eg: 
   ```
   !:N <Event> <Separator> <Word>
      ! Reprersents command line 
      != the most recenet command line
    :N  Represents a word on the command line 
         0 = command 1 = first argument etc
   ```

 ## Installing software ##

 #### RPM packages (Redhat Package Manager) ####
   ```
   yum search string         - Search for string
   yum info [package]        - Display info
   yum install [-y] package  - install package 
   yum remove package        - Remove package  
   rpm -qa                   - List all installed packages
   rpm -qf /path/to/file     - List the file packages
   rpm -ql package           - List packages files
   rpm -ivh package.rpm      - Install package
   rpm -e <package-name>     - Erase (uninstall) package
   ```
  #### DEB Distros ####
  ```
  apt-cache search string       - Search for string
  apt-get install [-y] package  - Install package
  apt-get remove package        - Remove package, leave configuration
  apt-get purge package         - Remove package, deleting configuration
  apt-cache show package        - Display information about package
  dpkg -l                       - List installed packages
  dpkg -S /path/to/file         - List files package
  dpkg -L package               - List all files in package 
  dpkg -i package.ded           - Install package
  ```



 
  ## apt-get Install files ##
  
1. **"apt-get install <name of appplication>"** -- install the the application 
    eg:  apt-get install bluefish || sudo apt-get install bluefish 
2. **"apt-get remove <name of appplication>"** -- remove the the application 
    eg:  apt-get remove bluefish || sudo apt-get remove bluefish 
3. **"apt-get cache search <filename>"** -- this will search all the files with name bluefish
4. **"apt-cache policy gimp"** -- this will display the installed and version 
5. **"sudo dpkg -i ./<filename>"** - unpack deg file and install it. make sure your are in right folder
 
 ## Other Command ##

1. **"rm-d bar"** - will only delete empty directories.
2. **"cat baz"** - This will print out the entire contents of baz to the terminal.
3. **"less baz"** - This will also print the contents of baz, but one terminal page at a time, beginning at the start of the file.
4. **"touch foobar"** - This creates an empty file with the name foobar in your current working directory. The contents of this file are empty
5. **"mv foobar fizzbuzz"** - stands for “move” and it can move a file or directory from one place to another.
6. **"cp fizzbuzz foobar"** - cp stands for copy By copying fizzbuzz to a new file called foobar, we have replicated the original file in a new file with a different name.
7. **"nano foobar"** - This will open up a space where you can immediately start typing to edit foobar.
8. **"rm fizzbuzz"** - Unlike directories, files are deleted whether they contain content or not.

 ## Disk management ##

 #### Partitions #### 
 * Disk can be divide into parts called partitions, Partitions allow you to seperate data 
 * Having seperate partitions is one way to prevent one part of the system.
 #### Partition tables ####
 1. #### MBR (Master Boot Record) ####
 * Can only address 2 TB of disk space
 * 4 primary partitions
 * Extended partitions allow you to create logical partitions
  2. #### GPT ####
 * GPT = GUID Partition Table, GUID = Global Unique Identifier
 * Replacing the MBR Partitioning scheme
 * Part of UEFI, UEFI is replacing BIOS
 * Extended partitions allow you to create logical partitions
 * Not supported on older OS, May require newer or special tools
 
 #### Mount Points ####
 * A directory used to access the data on a partition
 * /(slash) is always a mount point
 * /home
     * /home/jason is on the partition mounted on home

 ## Logical volume manager ##
 
 * Flexible Capacity - We can create file system that extend across multiple storage devices
 * Expand or shrink file system in realtime while the data remains online and fully accessible
 * Easily migrate from one storage device to another while online
 * Data mirroring
 * 
  #### Create,remove migrate a PV ####
  
 * Physical Volumes - PV/pv
 * Volume Groups    - VG/vg
 * Logical Volumes  - LV/lv

  ```
   pvcreate <path to storage path>                    - to create PV
                                                        eg: pvcrate /dev/sdb
   pvs                                                - list of pv
   vgcreate <vg filename> <path>                      - use to create vg 
                                                        eg: vgcreate vg_app /dev/sdb
   vgs                                                - to view vg 
   lvcreate -L <filesize> -n <lv name> <vg filename>  - to create Lv(Logical volumes)
   lvdisplay                                          - Display the details of lv 
   mkfs -t ext4 <path>                                - Top create file system
                                                        eg: mkfs -t ext4 /dev/vg_app/lv_data
   mkdir <path to mount>                              - to mount
   mount <path> <path to mount>                       - mount the fs
   df -h <path to mount>                              - display list of file system
   vgextend <file name> <path>                        - to extend the vg
                                                        eg: vgextend vg_app /dev/sdc
   lvmdiskcan                                         - Shows all storage devices to use 
   unmount <path to mount>                            - to unmount the fils system
                                                         eg: umount /secrest
   lvremove <path>                                    - to remove the lv
                                                         eg: lvremove /dev/vg_safe/lv_secrets /secrets
   vgreduce  <filename> <path>                        - to reduce/remove vg 
                                                        eg: vgreduce vg_safe /dev/sde
   pvremove <path>                                    - remove vg 
                                                        eg: pvremove /dev/sde
   vgremove  <filename>                               - to remove vg
                                                        eg: vgremove vg_safe
   pvmove <source> <destination>                      - to migrate data
                                                        eg: pvmove /dev/sdb /de/sde
  ```

 ## Manage User and groups ##

 * We can have multiple accounts in associated with OS 
 * Each Account as username, UID(unique ID), password etc
 * Case senstive
 * Username are usually less than 8 character, are case senstive 
 * Passwords are stored encrypted in /etc/shadow
 * /etc/shadow is only readable by root
 * UIDs, Root account UID is 0. 
 * GID - group ID 
 ```
 useradd[options] username
 -c "COMMENT"            - comments for account
 -m                      - create the home dire tory
 -s/shell/path           - The path to the users shell.
 groups username         - to know the group
 passwd <username>       - to create password using passwd
 -g GROUP                - Specify the default group
 -G GROUP1,GROUPN        - Additional groups
 -r                      - Create a system account
 -d <path>               - Specify the home directory
                           eg: -d /home/dir
 userdel [-r] <username> - to delete user home directory account
          Modify user account
 usermod [options] username
 -c "COMMENT"            - comments account
 -g GROUP                - Specify the default group
 -G GROUP1,GROUPN        - Additional groups
 -s/shell/path           - Path to the user shell
 ```
 *Groups 
 ```
 groupadd [options] <groupname>      - to create group with default GID
 groupadd -g <idvalue> <groupname>   - to create group with idvalue has GID
 groupdel <groupname>                - to delete group
 groupmod [options] <groupname>      - to modify the group name/id
 groupmod -g <gid vlaue>             - to change the GID value
 groupmod -n <group name>            - to change the Group name
 ```

 ## Special Permissions ##
 
 #### Setuid ####
 * When a process is  started, it runs using the starting users UID and GID
 * Setuid = set user ID upon execution regardless of owner
 * ping - need privillages to access network devices setting the setuid bit and having root as the owner of the file and lets anyone on the system successfully use ping coommand
 * chsh - command allows the user to change their shell 
 ```
   Adding setuid attribut 
 chmod u+s /path/to/file
 chmod 4755 /path.to.file
   removing th setuid attribute 
 chmod u-s /path/to/file
 chmod 0755 /path/to/file
    finding the setuid files
 find / -perm /4000 -ls
 
 ```
 #### Setgid ####
 * setgid = set group ID upon excution 
 * same as setuid
 ```
     finding the setgid files
  find / -perm /2000 -ls
     Adding setuid attribut 
 chmod g+s /path/to/file
 chmod 2755 /path.to.file
     removing th setuid attribute 
 chmod g-s /path/to/file
 chmod 0755 /path/to/file
 ```

 ```
      Adding the setuid and setgid
  chmod ug+s /path/to/file
  chmod 6755 /pat/to/file
 ```
 
 #### Sticky bit ####
 
 * Use on a directory to only aloow the owner of the file/directory to delete it 
 ```
     Adding setuid attribut 
  chmod o+t /path/to/file
  chmod 1755 /path.to.file
     removing th setuid attribute 
  chmod go-t /path/to/file
  chmod 0777 /path/to/file
 ```
