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


 ## Basic Commands ## 
 
1. **pwd** -- displays the current directory 
2. **cd** -- use to change directory 
   i) **cd ./<filename>** -- use to specfic an absolute path 
   ii) **cd ../** -- use to go to parent folder 
  iii) **cd ~** -- use to go to Home
3. ** ls ** --show which all files are present in the order
   i) **ls -l** -- gives the list  of files with created date 
  ii) **ls -r** -- gives the folder name in reverse order 
 iii) **ls -p** --  append / indicator to directories

 ## Administrative privileges in terminal ##
 
1. when we try to edit permission denied files we cannot edit file directly for such cases we use command "** sudo nano ./<filename> **"
2. **sudo !!** -- is use to run the pervious sudo commands
3. **sudo su** -- is use to change the user of computer it becomes rootuser you can edit all the files

  ## apt-get Install files ##
  
1. **apt-get install <name of appplication>** -- install the the application 
    eg:  apt-get install bluefish || sudo apt-get install bluefish 
2. **apt-get remove <name of appplication> ** -- remove the the application 
    eg:  apt-get remove bluefish || sudo apt-get remove bluefish 
3. **apt-get cache search <filename> ** -- this will search all the files with name bluefish
4. **apt-cache policy gimp ** -- this will display the installed and version 
5. **sudo dpkg -i ./<filename> ** - unpack deg file and install it. make sure your are in right folder
