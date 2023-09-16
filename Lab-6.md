## OS 2 : Lab #6
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕

- To change the owner of a file
````shell
sudo chown arafat file.txt
````

- To change the group of a file
````shell
sudo chown :root file.txt
````

- To change both the owner and group of a file
````shell
sudo chown arafat:roo7 file.txt
````

### Linux Processes :

- Process has an `ID` which consists of up to 5 digits
- Processes have two types: 
1) `Foreground` : must be finished before user could use terminal {ex: [ls]}
2) `Background` : allow user to continue to use the terminal

First process that starts on system called > systemd with `ID = 0`

> Note: a process that ends with [`d`] means it's a background one

- Background process = Daemons Process

- When a process create another process, first one is called `parent`
while created one is called `child`


- Show all processes running in the system
````shell       
ps -ef
````
````
UID|PID|PPID
 x   y   z
````
> `UID` > User who created this process <br>
> `PID` > Process ID <br>
> `PPID` > Parent process (who created it)


- Show processes that are created by specific user
````shell       
ps -u <Username>/<UserID>
````

- To make terminal sleep for [`n`] seconds (no command will be executed at this time)
````shell
sleep n
````       
> n is number of seconds for example : `sleep 5`

- Start a process in Background
````shell
sleep 1000 &
````
> `&` sign

> Note: To terminate a running command (like `sleep 1000`) use: <br>
> `Ctrl + c` > It terminates process <br>
> `Ctrl + z` > It stops process (pause)


- To terminate a process
````shell       
kill -option <ProcessID>
````
option (Called signals) may be :
- `-15` : softball (terminal) (if no other process depends on it)
- `-9` : hard-kill, used when [-15] is not working (Force)
- `-19` : stop a process (as Ctrl + z)
- `-18` : Resume a process

- Example:
````shell
kill -9 1272
````

- Terminate all sleep process in system
````shell
pkill -9 sleep
````

- Show all processes running in background only (when you used `&` in command)
```shell
jobs
```
> O/P : `[1] + Running sleep 1000 &`

- Transfer a process from background to foreground
````shell
fg %n
````
> Example: `fg %1` > Number [`1`] is from output of `jobs`

- Resume a process
````shell       
kill -18 1633
````

- Search for a specific process by its name (like `grip` command)
````shell       
pgrep -x -u 1000 -l docker
````
> `-x` : Search for an exact name (docker != dockermanager) <br>
> `-u` : Search for a process with its `UserID` who created it <br>
> `-l` : print `PID` + Process `Name`

### Inode & Softlink & Hardlink :

- Each file system (partition) has an Inode table, in which all the used
Inodes are mapped to particular files
- Linux stores administrative data about files in nodes
- Information stored in the Inode table are : 
1. Size 
2. DeviceID 
3. UID 
4. GID 
5. Mode 
6. Time Stamp 
7. pointer to date 
8. type of file 
9. file permission 
10. Number of hard links

- Inode tables do not contains filename of its content
- Names are stored in the Directory
- Each filename knows which Inode it has
- An Inode does not know which name it has, it just knows how many names are
associated with the Inode, those names are referred to as `Hard Links`

- To know Inode Number of a File/Directory
````shell
ls -id/-i <Filename/DirName>
````
> `-id` : For a Directory <br>
> `-i` : For a File


> `Soft link (Symbolic)` is like shortcut in windows

- Create a Soft Link
````shell
ln -s file1.txt softlink_file1.txt
````
> `ln` : stands for links <br>
> `-s` : for softlink

- Note: Inode Number of `file1.txt` != `softlink_file1.txt`
````shell
ls -l softlink.txt
````
> O/P > `L rwx|rwx|rwx` (`L` stands for link)

> Note: If main file is deleted then softlink file become useless

- Create Hard Link
````shell
ln file2.txt hardlink_file2.txt
````
> Note: Inode Number of `file2.txt` == `hardlink_file2.txt` <br>
> `Hardlinks` are used to backup files

````shell
    Disk
    ----
    ----  <------ File <----- Softlink
    ----


    Disk
    ----
    ----  <------ File
    ----  <----- Hardlink

(Refer to same partition in Disk)
````
> Note : You cannot use `hard link` across partitions because each partition  has its own Inode table
- You cannot make a hard link for a Directory
- To get information about Inode of your partition
````shell
df -i <Partition>
````
> Example: `df -i /dev/sdu5`

### Archiving & Compression :

- The `tar` command archive files to and extract files from a single
file called a tar file
````shell
tar -option <ArchiveName> file1,file2,...
````
> option can be : <br>
> `-c` > Create a new tar file (archiving) <br>
> `-t` > List table of content of a tar file <br>
> `-x` > Extracts files from the tar command <br>
> `-f` > Specify the archive file (used with archiving files or un-archiving files) <br>
> `-v` > Verbose mode (more information)

- Create a tar file (archive)
````shell
tar -cf archive.tar file1
````

- Show files in an archive file
````shell
tar -tf archive.tar file1
````

- To extract files
````shell       
tar -xf archive.tar
````

- To extract files in another path
````shell       
tar -xf archive.tar -C /home/arafat/Documents
````
> Or just execute command in this path



> Note: `touch file1; mkdir Dir1` Or `touch file1 && mkdir Dir1` <br>
> To execute more than one command in the same line 
> `&&` sign means that the first command have an error second 
> one won't be executed (like Programming)



### Compression :


- To compress a file 
````shell
gzip file1
````
> File will be taken to create zip file (file will disappear) <br>
> `gzip Dir1` (Wrong) -> Cannot make a compressed Directory

- Create a zipped & compressed file   
````shell      
tar -czf file.tar.gz dir7 file2.txt
````
> `-z` : stands for zip

- Unzip a zipped file
````shell       
gunzip file.tar.gz
````
> Then the file will become file.tar (use again `tar -fx` command)

- To make them just in one step
````shell
tar -xf file.tar.gz
````
