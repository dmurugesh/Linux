 ## Table of Contents ## 
 
 1.  Wildcards
 2.  Input, Output and Redirection 
 3.  Comparing Filies
 4.  Searching in filies and using Pipes
 5.  Transferring and Copying Files over the Network
 6.  Customizing the Shell Prompt
 7.  Shell Aliases
 8.  Enviroment Variables
 9.  Process and Job Control
 10. Scheduling Repeated Jobs with Cron
 11. Switching user and running commands
 12. Shell history and Tab completion
 13. Installing Software


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
       [!]    - Matches any of the characters Not included between the brackets. Matches exactly one character
                eg: [!aeiou] reult such as baseball,cricket
      [a-g]   - Matches all files that start with a,b,c,d,e,f or g
      [3-6]   - Matches all files that start with 3,4,5 or 6
      \        - Escape character use if you want to match a wildcard character
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
   2>file   Redirect standard error to a file
   null    Redirect output to nowhere
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

 ## Scheduling Repeated jobs with cron ##

 * Cron - A time based job scheduling service.
 * Crontab - A program to create, read, update and delete your job schedules 
 * Use cron to schedule and automate task
 * Each line in crontab represent two pieece of information 
    i) When to run it 
   ii) What to run 
 * cronatab manipulates the cron jobs.
   ```
   crontab file - Install a new crontab from file
   crontab -l   - List your cron jobs
   crontab -e   - Edit your cron jobs
   crontab -r   - Remove all of your cron jobs
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
  
  
   ## Table of Contents ## 
 
 1.  Wildcards
 2.  Input, Output and Redirection 
 3.  Comparing Filies
 4.  Searching in filies and using Pipes
 5.  Transferring and Copying Files over the Network
 6.  Customizing the Shell Prompt
 7.  Shell Aliases
 8.  Enviroment Variables
 9.  Process and Job Control
 10. Scheduling Repeated Jobs with Cron
 11. Switching user and running commands
 12. Shell history and Tab completion
 13. Installing Software


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
       [!]    - Matches any of the characters Not included between the brackets. Matches exactly one character
                eg: [!aeiou] reult such as baseball,cricket
      [a-g]   - Matches all files that start with a,b,c,d,e,f or g
      [3-6]   - Matches all files that start with 3,4,5 or 6
      \        - Escape character use if you want to match a wildcard character
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
   2>file   Redirect standard error to a file
   null    Redirect output to nowhere
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
