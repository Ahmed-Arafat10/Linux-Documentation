# OS2 : Lab #1
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕

- man a manual to help with commands
```
man ls
```
> press `q` button to exit man.

- print working directory (your current path)
```
Pwd
```

- list the files in the current directory
```
ls
```

Some `flags`/`options` with `ls` command:
- `ls -l` displays lots of information
- `ls -t` sort by modification time
- `ls -S` sort by size
- `ls -h` list file sizes in human-readable format
- `ls -r` reverse the order
- `ls *.pr` list `.pr` files only.

> `VIP Note` : `flags`/`options` in `Linux` are used to enhance the command

> Also Note: `Options` can be combined: `ls -ltr` instead of `ls -l -t -r`

- change to a specific directory
```
cd Music
```

- `cd ..` return to the previous directory ”as back button” if you are in `/home/arafat` and
  typed `cd ..` you return to `/home`


- go to your home directory
```
cd ~
```
> `tilde` sign `~` is the location of your home directory, example for user `arafat` home directory is `/home/arafat` and so on

- Create a new directory
````
mkdir cic
````

- remove an **_empty_** directory
````
rmdir cic
````

- remove all files and directories in a folder.
````
rm –r cic
````

- To clean terminal from all commands
````
clear
````

- List all `files`/`folders` [Even hidden file]
````
ls -a
````

## 1. Full Path vs Relative Path:
<hr>

#### 1.1 change directory using Full path
````
cd /home/ahmed/music
````

> `VIP Note` : in full path you MUST start with `/`   [`root` sign]

> also note `cd ~` is same as `cd /home/user`

#### 1.2 Relative path : 
````
cd music 
````
> I'm already in `/home/ahmed`, it means that inside `ahmed` folder there is a folder called `music`

````
cd ../../Download
````
> means from my current location go back TWICE then in this directory there is a folder called `download` 

> example if current path is `/home/arafat/OS2/LAB_1`, then Linux will go to `arafat` folder (go back two times from current folder) then go to folder called `Download` that exists in `arafat` folder  

> `..` is a relative path

- Create Dir. called `Dir1` in current Dir. and create another Dir. called `Dir2`
but in previous Directory (folder)
````
mkdir Dir1 ../Dir2
````

- Show date
````
date
````

- To show calender of current year
````
cal
````

- Show all 12 months pf 1990 year
````
cal 1990
````

- To create Directory/Folder 
````
mkdir <NameOfDir>
````

- To create a file
````
touch <FileName> <File2Name>
````