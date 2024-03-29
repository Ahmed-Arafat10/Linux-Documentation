# Session #2


String Processing :
---------------------

inside /etc/passwd
- ```username:password:UID:GID:comment:homepath:terminalpath```
- [:] Called separator(delimiter)

- Count characters in a file
```
wc <FileName>
```
Eample:
```
wc /etc/passwd
```
O/P: ```47 82 2783 /etc/passwd```
- Line Word Character respectively

```
wc -c -l -w /etc/passwd
```
> c : Character <br>
> l : Line <br>
> w : Word <br>

- Search for lines that contain a specific text in a file
```
grep <TextToSearch> <FileName>
```
Example:
```
grep ahmed /etc/passwd
```
- Search for lines that starts with a specific text in a file
Example:
```
grep ^ahmed /etc/passwd
```
- Search for lines that {ends} with a specific text in a file
Example:
```
grep ahmed$ /etc/passwd
```

- Search for lines that contain a specific insensitive text in a file
Example: 
```
grep -i ahmed /etc/passwd
```
> -i for insensitive, it may be Ahmed or ahmed

- Search for lines that contain a specific text in all files in Cur. Dir.
```
grep -r Dir1
```
- Search for lines that {Do not} contain a specific text in a file
```
grep -v ahmed /etc/passwd
```
> Invert (Not Contains) <br>
> Work also with [-r] (folders)

- To sort lines in a files
```
sort -T: -k -n <FileName>
```
> -T: Means that separator is [:] <br>
> -k Number of Field to sort with <br>
> -n : treat field as a No. if it is a No. not as string (ASCII) {1 Not '1'} <br>
Example:
```
sort -T: -k3 -n /etc/passwd
```
Note: add [-r] flag to reverse sort
> ```sort``` doesn't change file, it just changes output (how its shown in terminal)

```
sort -T: -k1 -n /etc/passwd > sortedGroup.txt
```
> Save output of first command as a text in file called sortedGroup.txt

- Show only first,third (for example) fields for each line
```
cut -d: -f1,2,3,--- <FileName>
```
Example: 
```
cut -d: -f 1,3 /etc/group
```
- Just Print text in terminal
```
echo hello world
```
- Save text in a file
```
echo hello world > fil1.txt
```

Piping & Redirection:
-----------------------

```
ls /etc | more
```

```
ls /etc | grep passwd
```
> [|] pipe character
       
- Its like executing first command and save it's output in file instead of showing in in terminal
            then passing this file to second command after pipe character [|]

```
sudo ls -R / | grep shadow
```
> -R / Means to show all files/Dir. inside root [/] and also inside each Dir.
show its files/Dir and so on, so it outputs all files/Dir. in OS
- sudo : means {super user do}

- 'Tee' reads the standard input and writes it to both the standard output (terminal) 
and to save output in a a file + showing output in terminal (if I want)
     
- it shows output + saving output in a file
```
ls /etc |tee file.txt
```
Examples:
```
ls /etc | tee etc_content.txt
```

```
cat /etc/passwd | grep ^ahmed |tee file.txt | wc -l
```
> O/P: 1
> 
- Commands are like water running in a pipe
        

Redirection :
--------------

- Save text in a file (Override it's content)
```
echo arafat > fil1.txt
```        

- Concatenate (append) text in a file {in new line} as str = str+text
```
echo is my best friend >> file1.txt
```

```
cat file1.txt
```
> O/P: arafat <br>
> is my best friend  {in new line}

- It only save errors in err_file instead of printing it + printing other paths files (which don't have errors)
so, its redirecting error in a file instead of printing them
```
ls /fooo 2> err_file
```
- Concatenate (append) text in a file in new line as str = str+text but for redirecting error
```
ls /fooo 2>> err_file
```
- Will only print errors and save rest in fileX.txt, redirecting standard output (terminal)
```
ls / > fileX.txt
```
- Will redirect both standard errors and standard output
```
ls > fileX.txt 2>&1
```
> 1 : standard output <br>
> 2 : standard error <br>
> & between them <br>

- Note: ```>``` is same as ```1>```



```
mail -s "Subject" arafat@gmail.com < FileName
```
> [<] called standard input redirection <br>
> Means that you take text in FileName as an input for command <br>
> FileName contains body of mail (instead of writing body in command) <br>
> Install its package first <br>


VI Editor:
------------
- Only editor available in rescue mode (as safe mode in windows)

```
vi file.txt
```

- hit [i] to enter insert mode
- hit [esc] to enter command mode

- In command mode:
   - :q! -> to Quit
   - :wq! -> to Write and then quite
   - :w! -> to Write (save)
   - You can use up/down/right/left buttons in command mode

- Also In command mode:
   - hit [yy] : to copy a line
   - hit [dd] : to cut a line
   - hit [pp] : to paste a line
   - hit [p OR P] : to paste copied line, small p to put copied line under cur line and big P to put it above
   - hit [D] -> Delete a line (from cursor to end of line)  H[e]llo wolrd -> H      
    -----------
   - :n,nd -> Delete Range of lines
   - :%d -> Delete all lines
   - /text -> to highlight text in file
   - hit [enter] then [n]down or [N]up to traverse along highlighted text
   - :set nu -> To show number of lines
```
1
2
3
```
   - :set nonu -> to hide number of lines


Environment Variables:
-----------------------
```
x = arafat
echo $x
```
> O/P: arafat

```
echo $PWD
```
> O/P: /home/arafat/Document
```
echo $USER
```
O/P: arafat
```
echo $SHELL
```
> O/P: /bin/bash <br>
> For type of shell, its bash here <br>
> bash : means born against shell <br>

```
export CURRENT_USER = arafat
```
> Export is used to create environment variables, best practices is to name it with upper case

```
echo CURRENT_USER
```
> env USER (X)  WRONG

``` printev current_user ``` -> no need to $ sign

- Note: this is only for current terminal (not permanent), to solve this save it in initialization files ```~/.bashrc```

```
nano ~/.bashrc {save it here}
```
- To execute it or just close all terminals (as you are reloading page in web so changes can take place)
```
source ~/.bashrc
```
- To print all environment variables
```
printenv
```
OR
```
env
```

- To remove variable
```
unset <VariableName>
```
Example:
```
unset CURRENT_USER
```


Command Quoting:
------------------

```
echo $PWD   
```
> Will print path
```
echo "$PWD"
```
> Will print path
```
echo '$PWD'
```
> Will print [$PWD] as text <br>
> single quote ignores all meta-character
```
echo '\$PWD'
```
> Will print [\$PWD] as text
```
echo "\$PWD"
```
> Will print [$PWD] as text <br>
> Back slashh ignores next meta-character in Double quotes
```
echo "Today date is" $(date)
```

```
$ rm -r $(ls) = rm -r *
```

```
$ history
```
> All commands written by you is saved in ~\.bash.history
- ```!!``` -> execute previous command
- ```!n``` -> Example: ```!350``` -> execute command No. 350 in history
- ```!-n```-> Example: ```!-2``` -> previous previous Command (n Times)
```
alias q = "ls -a"
```
> Remember not permanent, save it in ```~/.bashrc``` to become permanent
```
$ q
```
> Execute alias
    
- Note: if you name it foe example as ```ls```, t it will execute it not default ```ls``` command, to fix 
it instead of closing terminal use ```\ls``` backslash ls



