## OS2 : Lab #2
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕

- create a new blank file
````
touch file.txt
````

- create a new blank files (two or more)
````
touch file1.txt file2.txt
````

- create a file (if not exists yet) then enter a text editor to add your texts in this file
````
nano file.txt
````

- output content of a file in the terminal
````
cat lab.txt
````

- displays the top lines of a file `By default the first 10 lines`
````
head file.txt 
````

- display first 50 line of a file
````
head -n50 file.txt
````

- Same as head, but shows the last lines 
````
tail file.txt
````

- display last 50 line of a file
````
tail -n50 file.txt
````

- Show part of text, then you hit `enter` button to show next part and so on, used when a file contains many lines
````
more <FileName>
````

- copy a file on same directory and change name of new copy
````
cp f.txt f2.txt
````

- copy a file in a previous directory
````
cp f1.txt ../cic
````

- copy a directory
````
cp -r STLs cic
````
> `r` tag stands for recursive

- copy multiple files at same time in cur. Dir.
````
cp ./{file1,file2}  ./Document
````

- copy more than one file in a directory
````
cp  file1 file2 ./Document
````

- move a file to a `home directory` location
````
mv f1.txt ~/cic
````

- move `f1.txt` file to previous folder 
````
$ mv f1.txt ../cic 
````

- `mv` command can also be used to rename a file
````
mv f1.txt f2.txt
````

- remove a file
````
rm lab.txt
````

- show a confirmation message (answer with `y`/`n`) first
````
$ rm -i <FileName>
````

- Remove all files only in current folder
````
rm *
````

## File Globbing :
<hr>

- Remove any file ends with `.txt`
````
rm *.txt
````

- Remove any file as `aoo`/`boo`/`coo` etc.
````
rm ?oo
````

- Remove `file1`,`file2`,`file3` files
````
rm file[1-3]
````

- give the user the permission to write
````
chmod u+w lab.txt
````

- remove the `execute` permission from group
````
chmod g-x lab.txt
````

- meaning of `r`/`w`/`x`
  - `r` > `read`
  - `w` > `write`
  - `x` > `execute`


- meaning of `u`/`g`/`o`/`a`
  - `u` > `user`
  - `g` > `group`
  - `o` > `others`
  - `a` > `all`
