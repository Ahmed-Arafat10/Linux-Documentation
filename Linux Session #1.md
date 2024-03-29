# Session #1

- Kernel is a computer program that is the heart and core of
an operating system
- Kernel is responsible for low-level tasks as disk management,
memory management and task management.
````
  -----------
  Application
  -----------
    Kernal
-----------------
CPU|Memory|Device
-----------------
````

- Why linux ?
  1. FOSS {free open source software}
  2. secure
  3. stability and performance

- Distribution Of Linux (Distro) is an OS that is formed from a collection of softwares that is based upon the linux kernel.



- Linux File Hierarchy
````
                        / ----root
        /bin     /proc      /boot    /etc   /home     /lib    /var
    All package             So device       users
    of system               can open       of system

````


## Linux Commands

- Print working directory (your current path)
```
pwd
```
> O/P : /home/arafat


- man a manual to help with commands
```
man ls
```
> press `q` button to exit man.


- To clean terminal from all commands
```
clear 
```
> (OR) ```ctrl+L```




- List content of current Directory
```
ls
```

- List content of specific Directory
```
ls /home
```

- List all files/folders {Even hidden file}
```
ls -a
```
> flag(option) : enhance/improve command

- Note: any file starts with dot (.) means hidden file.
```
ls -a /home
```

- Change Directory
```
cd /etc
```

- Go back one Dir. from your current Dir.
```
cd ..
```
>  /home/ahmed -> /home/


Full path vs relative path:
-----------------------------

- Full : cd /home/ahmed/music
> start with / {root} <br>
> cd ~ {= /home/user}

- Relative : cd music {I'm already in /home/ahmed}
> cd ../../Download

- {..} is a relative path

- Create Dir. called cd in current Dir. and create Dir. called Test1
but in previous Dir.
```
mkdir cd ../Test1
```

```
cd ./Downloads
```
> ./Download means from cur. Dir. go to Download

- Open manual for specific command
```
man <Command>
```
Example:
```
man ls
```
OR
```
whatis <Command>
```
Example: 
```
whatis ls
```

- Show date
```
date
```

- To show calendar of current year
```
cal
```

- Show all 12 months pf 1990 year
```
cal 1990
```

- To create Dir/Folder
```
mkdir <NameOfDir>
```

- To create Dir. inside Dir. us [-p] flag
```
mkdir -p <NameOfDir>
```

- To create a file
```
touch <FileName> <File2Name>
```

- VIP Note: extension in linus is useless (don't affect file itself), but we use it
to make name of file Descriptive
- Example: file.txt , file.mp4 , file.png , file.gz
-    text          video     photo         zipped

- Avoid ><?*#  in file of a file
- Everything in linux is file, Dir. is specific file

- To show type of a file {whether text,video,image}
```
file <FileName>
```

- Copy a file from a Dir. to another Dir.
```
cp <NameOfFile>
```
Example: 
```
cp test1.txt   Document/folder1/
```

- To copy multiple files at same time in cur. Dir.
```
cp ./{file1,file2}      ./Document
```
OR
```
cp  file1  file2        ./Document
```

- To copy one Dir. into another
```
cp  -r  <folderFrom> <folderTo>
```
> -r :  Recursive

- Will show a confirmation [N/Y], as it will override any other file with same name in Cur. Dir.
```
cp -i file.txt ./folder1
```

- To move a file to specific location
```
mv <FileName> <Distination>
```
Example: 
```
mv file11.txt folder2
```

- Will copy a file to my destination + renaming copied one to copy.txt
```
mv copy.txt  /home/arafat/Desktop/file123.txt
```

- Rename copy.txt to file123.txt
```
mv copy.txt  file123.txt
```

- To remove a file
```
rm <FileName>
```

- To show a confirmation first
```
rm -i <FileName>
```

- To remove a Dir.
```
rm -r <FileName>
```

- Used to remove empty Dir. only
```
rmdir <DirName>
```

- Remove all files Dir. in Cur. Dir.
```
rm * -r
```

- Remove all files only
```
rm *
```

Command for reading a file:
-----------------------------

- To show text in a file
```
cat <FileName>
```

- Show part of text, then you hit enter to show next part and so on , used when file text is large
```
more <FileName>
```
> space: scroll down <br>
> p: scroll up <br>
> q: to quit <br>

- Show first 10 lines
```
head <FileName>
```

- Show first 5 lines
```
head <FileName> -n 5
```

- Show last 10 lines
```
tail <FileName>
```

- Show last 5 lines
```
tail <FileName> -n 5
```

- To write on a file inside terminal
```
nano <FileName>
```
> ctrl(^) + x : exit <br>
>ctrl(^) + o : write out (Save As) <br>



File Globeing :
---------------

- Remove any file ends with [.txt]
```
rm *.txt
```

- Remove any file as aoo/boo/coo ...
```
rm ?oo
```

- Remove file1,file2,file3
```
rm file{1..3}
```
OR
```
rm file[1-3]
```

- Read the content of a text file one page (one screen) at a time. It has faster access because if file is large it doesn’t access the complete file, but accesses it page by page
```
less command
```
