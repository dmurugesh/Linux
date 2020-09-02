 ## Table of Contents ##

 1.  Disk management
 2.  Logical volume manager
 3.  Special Permissions
 4.  TCPIP Networking
 5.  Shell scripting


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

 ## TCPIP Networking ## 

 #### TCP/IP ####
 * TCP/IP - Used for network communications 
 * TCP = Transmission Control Protocol, IP = Internet Protocol
 * TCP - controls data exchange 
 * IP - sends data from ine device to another 
 * Hosts - device on a network that have an IP address
 * TCP is used to exchange data between devices
  #### IP ####
 * Consits of four octets seperated by dots.
 * IP address consists of two parts, first part is network address and second part is host address
 * Network portion of IP address tells the router what network the host belongs to.
 * The host address tells router the specific device that data to be delivered to.
   
   Classsfull networks 
   ![Linux Directories](/Notes/img/classfullnetworks.png?raw=true "Title")
   
   subnet mask 
   ![Linux Directories](/Notes/img/subnetmask.png?raw=true "Title")
   
   broadcast address
   ![Linux Directories](/Notes/img/broadcastadd.png?raw=true "Title")

 * Classless Inter-Domain Routing / CIDR 
   Reserved Private Address space
  ![Linux Directories](/Notes/img/reservedprivatenetworks.png?raw=true "Title")

 #### DNS and hostname ####
  ```
   ip addr   	  - To view the ip address
   ip a      	  - To view the ip address
   ip a s    	  - To view and show the ip address
   ifconfig  	  - To view ip addres  s 
   hostname      - To display the hostname 
   hostname -f   - To display fully qualified domain name
   host           - To look up DNS or ip address 
                     eg: host www.mycompany.com, host 1.2.1.6
                       
  ```
 * Loopback device is used to communicate with your own linux system ip address 127.0.0.1
 * Host is device connected to network
 * DNS - Somain name system
 * The primary purpose of DNS is to human readable names into IP address. DNS does the reverse as well
 * FQDN = full qualified domain name. contains a domain name and a top-level domain name. each section is divide by 'dot'
   eg: webprod01.mycompany.com
 * TLD top level domain 
   eg: .com,.net, .org
 * Domains 
   below (to the left of) TLD
 * sub-domain
   below to left of domain
   eg: webprod01.ny.us.mycompany.com
 
 #### Network ports ####
  ![Linux Directories](/Notes/img/networkports.png?raw=true "Title")

 * DHCP - Synamic Host Configuration Protocol
 * DHCP servers asssign IP address to DHCP 
 
 #### Ping ####
 ```
 ping <host name/ip>                      - to run ping command
 ping -c <count/packets> <host name/ip>   - to run ping command for specfic packets of data
 traceroute -n <host name/ip>             - to know if we expirencing DNS issues

 ```
 * traceroute - default transfer dns name into server 
 * The netstat command 
 * telnet HOST_OR_IP PROT_NUMER - use telnet to check connection 
  #### Netstat Commands ####
  ![Linux Directories](/Notes/img/netstat.png?raw=true "Title")

 ## Shell Scripting ##
 
 #### Scripts ####
 * Contains a series of command 
 * An interprete excutes commands in the script 
 * Anything you can type at the command line, we can put in a script
 * Great for automation task 

 #### variable ####
 * Storage locaton that have a name 
 * Varaible are case senstive
 * Variables can start with letters or undscores, cannot start with digits
 * 
  ```
  syntax =>  VARIALBE_NAME="Value"
  Test
  syntax => [ condition-to-test-for ]
           eg:  [ -e /etc/passwd ]
  -d <file>   - True if file is directory
  -e <file>   - True if file exits
  -f <file>   - True if file exits and is a regular file
  -r <file>   - True if file is readable to you
  -s <file>   - True if ile exists and is not empty 
  -w <file>   - True if the dile is writable by you
  -x <file>   - True if the file is excutable to you
     String operator(tests)
  -z STRING   - True if string is empty
  -n STRING    - True if string isnot empty
  STRING1 = STRING2 - True id  the string are equal
  STRING1 != STRING2 - True if strings are not equal 
  ```
 * Making decisions - ends with fi
  ```
  if [ condition is true ]
  then 
     command 1
     command 2
     command 3
  fi

        if-else 
  if [ condition is true ]
  then 
     command N
  else 
     command N
  fi

      if/elif/else
  if [ condition is true ]
  then 
     command N
  elif [ condition-is-true ] 
  then
     command N
  else 
     command N
  fi

     For loop - if want to perform in list of items 
  for VARAIBLE_NAME in ITEM_1 Item_N
  do 
    command 1
    command 2
    command N
 done
  ```
 
