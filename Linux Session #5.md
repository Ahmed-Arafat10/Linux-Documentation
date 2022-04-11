# Session #5




## System Administration




Sed utility :
------------

- Sed stands for streamline editor

- It does not change your file unless the output is saved with shell redirection by default

- Sed editor process a file (input) one line at a time and send output to the screen

- Sed stores the line it process in a buffer and once processing is finished the line
is sent to the screen (unless command wad to delete the line) and the next line is read
and the process is repeated until the last line is reached

Addressing :
------------
- Its used to determine whcih lines to be edited
Addressing format can be:
1) Number
2) Regular Expression
3) Both

- Sed command tells sed what to do with line whether:
1) Print it
2) Remove it
3) Change it


- Sed command format
```
sed 'Command' FileName
```

- Print lines that contains word "root"
``` 
sed '/root/p' myfile
```
> word is put inside backward slashes [/word/] <br>
> p -> For Printing the line that contains word


- Prevent default behaviour of Sed to print each line
```
sed -n '/root/p' myfile
``` 
 > -n : a flag


- Print only Line #1
```
sed -n '1p' /etc/password
```

- Print range from Line #1 to Line #10
 ```
sed -n '1,10p' /etc/password
```

- Print from Line that contains word "games" to line that contains word "root"
```
sed -n '/games/,/root/p' /etc/password
```

- Print all Lines except Line #3
```
sed -n '3!p' Myfile
```

- Delete Line #3 {Just in terminal not actual file}
```
sed '3d' Myfile
```

- Nothing will be shown in terminal
```
sed -n '3d' Myfile
```

- Delete all Lines that contain word "Hello"
```
sed '/Hello/d' Myfile
```

- Delete all Lines that starts with word "Hello"
```
sed '/^Hello/d' Myfile
```

- Delete all Lines that contain word "Hello" and then quite
```
sed '/Hello/d;/^Hello/q' /etc/password
```
> [;] : for more than one command <br/>
> q : to quite
> Note: not working with him


- Delete all Lines that ends with word "Hello"
```
sed '/Hello$/d' File2.txt
```

- To save file with new edit
```
sed -i '/^Hello/d' File2.txt
```
> Note: Not recommended to use it, as you deal with sensitive files like passwd,
so save your changes in another file {redirection}
```
sed -i '/^Hello/d' File2.txt > File2_Temp.txt
```

- To edit a pattern using sed, this command will change every "everybody" word
to "everyone"
```
sed 's/everybody/everyone' Myfile2
```
> s: stands for substitute

- If there are two "everybody" in the same line {ex: .... everybody .... everybody}
its going to just change first word and then break to next line without changing
other word in same line, to fix this
```
sed 's/everybody/everyone/g' Myfile2
```
> g: stands for global


- To print lines that are changed
```
sed -n 's/everybody/everyone/gp' Myfile2
```
> p : for print


- To delete from line #3 till the end
```
sed '3,$d' Myfile
```

- To make two Sed command in one line, this command will print from line #1
to line #3, then from line #6 to line #7

```
sed -n -e '1,3p' -e '6,7p' Myfile
```


------------
AWK Utility :
------------

- Named AWK for first letter of name of the three developer of it
- its a programming language used for manipulating data and generating reports
- AWK scans a file line by line, search for lines that match a specific patterns
and then performing selected action


- Awk command format
```
awk 'Instructions' FileName
```

- In Awk, Line = Record

- Important variables:
    1) ```FS``` -> you can control field separator {default is space but you can change it to
    colon [:] as in [/etc/passwd] }
    2) ```RS``` -> record separator which is '\n' by default
    3) ```$0``` -> Means entire record {$1 for field #1 , $2 for field #2 , etc ...}
    4) ```NR``` -> Means record number
    5) ```NF``` -> Number of fields in a record {7 as in passwd}


- Print first field for each line
```
awk -F: '{print $1}' /etc/passwd
```
> F: specify that field separator is [:]


- Print field 1,3 for each line
``` 
awk -F: '{print $1,$3}' /etc/passwd
```

- Print "Log name:" text with first field for each line
```
awk -F: '{print "Log name:",$1}' /etc/passwd
```
    
- Display whole file {like $ cat}
```
awk '{print $0}' /etc/passwd
```

- Display Number of each line along with line itself
``` 
awk '{print NR,$0}' /etc/passwd
```
   
- Display each line + Number of fields for each one
```
awk '{print $0,NF}' /etc/passwd
```

- BEGIN is executed one time before awk process any line from the input file
- It determines first value of FS,RS variables
```
awk 'BEGIN {FS = ":";RS="\n"} {print $0,NR}' 2-empty-spaces.txt
```

- END is executed one time after awk process all lines of input file
- It does not match any input line
```
awk 'END {print NR} {print NR}' myfile
```

Conditional Expression :
------------------------
```
if(expression1) {statement1;statement2}
else if(expression2) {statement1;statement2}
else {statement1}
```
Operators: <  <= == != >= > ~  !~ <br/>
~ -> Match a regular expression <br/>
!~ -> Not match a regular expression


Loops:
------

- While Loop
```
awk -F: '{i=1;while(i<=NF){print NF,$i;i++}}' /etc/passwd
```
> It will print 7 fields for each line, each in a new line
- For Loop
```
awk -F: '{for(i=1;i<=NF;i++){print NF,$i}}' /etc/passwd
```


```
awk '{ if($1 > $2) max = $1:
        else max = $2;
        print max}' texting.txt
```

```
awk '{ if($1 + $2 > 100) print $0 } 'Testing.txt
```

```
awk '{ if(NR == 4 || NR == 5) print NR ":" $0}' /etc/passwd
```



-------------
Shell Script :
-------------

- Standard Shells :
    1) Bourne shell (sh)
    2) C shell (csh)
    3) korn shell (ksh)

- Shell program is a combination of Unix commands + programming constructions and comments
- To execute the script use [$ chmod] command to turn on the execute permission for current user

-> First line starts with-> ```  #! /bin/bash  ``` <br>
-> Comment ->``` # Calculating x ```  <br>
-> Extension of it is [.sh]  <br>
-> $ nano day5.sh  <br>
- To run the script use:
    1) ``` ./days.sh```
    2) ```source dat5.sh``` {this method is better}
> Note: any file by default does not have execute permissions, so we have first to [$ chmod] command
```
chmod u+x day5.sh
```

Remember : ``` echo $path``` -> Shows all Directories that stores commands of Linux, each time you enter a command
then hitting enter button system check if the entered command is exist in any file in these Directories

- To make your script global {just enter his name and the press enter button}, use this command
```
export PATH = $PATH:/home/arafat/bash.script
```
> [:] as field separator of file $PATH is [:]
> To make this global to all terminals add above command to [~/.bashrc]


Variables:
----------
- Local Variables -> ```x=foo;echo $x```
> Note: x = foo is wrong {NO SPACES}
- Environment Variables -> ```export y=bat; echo $y```
- Predefined variables -> Defined already in bash script

 ```echo $? ``` -> output of last command [0/1] <br>
0 is for true {as ant c program return 0: when executed successfully} <br>
1 is false

```$#``` -> Number of argument  <br>
```$*``` -> list all arguments  <br>
```$1,$2 ,...``` -> first,second argument  <br>
```$0``` -> script name  <br>

EX: inside script.sh file
```
echo "script is $0"
echo "Number of arguments are $#"
echo "List arguments $*"
echo "Argument 1 = $1"
```
> run : $ script.sh arg1 arg2 arg3
- O/P:
```
script.sh
3
arg1 arg2 arg3
arg1
```

```
$ i=5                          O/P
$ echo $i                       5
$ i=$i+1; echo $i             '5+1'
$ let i=$i+2
$ echo $i                       7
$ typeset -i Num
$ Num=5:echo $Num               5
$ Num=$Num+5:echo $Num          10
```
