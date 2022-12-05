
**Session #4**
===============

- To change the owner of a file
       
      sudo chown arafat file.txt

- To change the group of a file

      sudo chown :root file.txt

- To change both the owner and group of a file

      sudo chown arafat:roo7 file.txt

Note: Its importance appears in system  2 course, not here


----------------
Linux Processes :
----------------

- Process has an ID which consists of up to 5 digits
- Processes have two types: 
1) Foreground : must be finished before user could use terminal {ex: [ls]}
2) Background : allow user to continue to use the terminal

First process that starts on system called -> systemd with ID = 0

Note: a process that ends with [d] means its a background one

- Background process = Daemons Process

- When a process create another process, first one is called parent
while created one is called child


- Show all processes running in the system
       
      ps -ef

O/P: UID|PID|PPID
      x   y   z

   UID -> User who created this process
   PID -> Process ID
   PPID -> Parent process {who created it}



- Show processes that are created by specific user
       
      ps -u <Username {OR} UserID>

- To make terminal sleep for [n] seconds {no command will be executed at this time}
$ sleep n
       
       sleep 5

- Start a process in Background
       
      sleep 1000 &
-> [&] sign

Note: to terminate a running command (like $ sleep 1000) use:
    Ctrl + c --> It terminates process
    Ctrl + z --> It stops process {pause}


       
      kill -option <ProcessID>
option {Called signals} may be :
- -15 : softkill (terminal) {if no other process depends on it}
- -9 : hardkill, used when [-15] is not working {Force}
- -19 : stop a process (as Ctrl + z)
- -18 : Resume a process

EX:       
    
    kill -9 1272
    
   - Terminate all sleep process in system {pkill}
    
    pkill -9 sleep


- Show all processes running in background only (when you used [&] in command)
```
$ jobs
```
> O/P : ```[1] + Running sleep 1000 &```

- Transfer a process from background to foreground
       
      fg %n
EX: fg %1    -> Number [1] is from output of `jobs`

- Resume a process
       
      kill -18 1633


- Search for a specific process by its name {like $ grip command}
       
      pgrep -x -u 1000 -l docker
> -x : Search for an exact name { docker != dockermanager} <br>
> -u : Search for a process with its UserID who created it <br>
> -l : print PID + Process Name

---------------
Linux Services :
---------------

- A service is an application or set of applications that run in Background
waiting to be used

- Show services in system
       
      systemctl
-> You can use it to show/stop/start a service
 {OR}
       
       service <ServiceName> <Action>
       
      sudo systemctl status docker
       
      sudo systemctl stop docker
       
      sudo systemctl start docker
- Enable/Disable auto start of a service when system boots
       
      sudo systemctl enable/disable docker


----------------------------
Inode & Softlink & Hardlink :
----------------------------

- Each file system (partition) has an Inode table, in which all of the used
Inodes are mapped to particular files
- Linux stores administrative data about files in nodes
- Information stored in the Inode table are : 
1) Size
2) DeviceID
3) UID
4) GID
5) Mode
6) Time Stamp
7) pointer to date
8) type of file
9) file permission
10) Number of hard links

- Inode tables do not contains filename of its content
- Names are stored in the Directory
- Each filename knows which Inode it has
- An Inode does not know which name it has, it just know how many names are
associated with the Inode, those names are referred to as {Hard Links}

- To know Inode Number of a File/Directory
       
      ls -id/-i <Filename/DirName>
-> -id : For a Directory
-> -i : For a File


-> Soft link (Symbolic) is like shortcut in windows

- Create a Soft Link
       
      ln -s file1.txt softlink_file1.txt
-> ln : stands for links
-> -s : for softlink

Note: Inode Number of [file1.txt] != [softlink_file1.txt]


       
      ls -l softlink.txt
O/P -> L rwx|rwx|rwx
        -> [L] for link

- If main file is deleted then softlink file become useless

- Create Hard Link
       
      ln file2.txt hardlink_file2.txt

Note: Inode Number of `file2.txt` == `hardlink_file2.txt`
      also Hardlinks used to backup files


    Disk
    ----
    ----  <------ File <----- Softlink
    ----


    Disk
    ----
    ----  <------ File
    ----  <----- Hardlink

(Refer to same partition in Disk)

Note : - You cannot use hardlink across partitions because each partition
has its own Inode table
- You cannot make a hard link for a Directory
- To get information about Inode of your partition
       
      df -i <FileSystem>
EX: $ df -i /dev/sdu5

-------------------------
Archiving & Compression :
-------------------------

- The {tar} command archive files to and extract files from a single
file called a tar file

       
      tar -option <ArchiveName> file1,file2,...
option is for: -c -> Create a new tar file {archiving}
               -t -> List table of content of a tar file
               -x -> Extracts files from the tar command
               -f -> Specify the archive file {used with archiving files or unarchiving files}
               -v -> Verbase mode {more information}

- Create a tar file{archive}
       
      tar -cf archive.tar file1
-Show files in an archive file
       
      tar -tf archive.tar file1

- To extract files
       
      tar -xf archive.tar

- To extract files in another path
       
      tar -xf archive.tar -C /home/arafat/Documents
{OR} just execute command in this path



Note:        
      
      touch file1; mkdir Dir1
   {OR}
      touch file1 && mkdir Dir1
-> To execute more than one command in the same line, but for [&&] sign
if the first command have an error second one wont be executed {like Programming}



Compression :
------------

- To compress a file
       
      gzip file1
-> File will be taken to create zip file {file will disappear}

       
      gzip Dir1 (X) -> Cannot make a compressed Directory

 -> Create a zipped & compressed file   
      
      tar -cfz file.tar.gz dir7 file2.txt
-> -z : stands for zip


- Unzip a zipped file
       
      gunzip file.tar.gz
-> Then file will become file.tar {use again $ tar -fx command}

- To make them just in one step
       
      tar -xf file.tar.gz
