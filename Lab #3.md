# OS2 : Lab #3
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕

- update a user’s authentication tokens
````
Passwd
````

- show the user who is currently logged in
````
Whoami
````

## String Processing :

inside `/etc/passwd` file
``
username:password:UID:GID:comment:homepath:terminalpath
``

>`:` Called separator (delimiter)

- Count characters in a file
````
wc /etc/passwd
````
> O/P: `47 82 2783 /etc/passwd`
- means `Lines` `Words` `Characters` respectively

- Search for lines that contain a specific text in a file
````
grep ahmed /etc/passwd
````

- Search for lines that starts with a specific text in a file
````
grep ^ahmed /etc/passwd
````

- Search for lines that ends with a specific text in a file
````
grep ahmed$ /etc/passwd
````
- Search for lines that contain a specific insensitive text in a file
````
grep -i ahmed /etc/passwd
````
> `-i` stands for insensitive, it may be Ahmed or ahmed

- Search for lines that `Do not` contain a specific text in a file
````
grep -v ahmed /etc/passwd
````

- To sort lines in a files
````
sort -T: -k3 -n /etc/passwd
````
> `-T:` Means that separator is `:`
>
> `-k` Number of Field to sort with
>
> `-n` : treat field as a number if it is not a number as string then order using `ASCII` code (`"1"` Not  `1`)

> `sort` doesn't change file, it just changes output (how its shown in terminal)


# Piping & Redirection
<hr>

````
ls /etc | more
````

````
ls /etc | grep passwd
````
> `|` is pipe character

- It is like executing first command and save it's output in file instead of showing in terminal
  then passing this file to second command after pipe character `|`

````
sort -T: -k1 -n /etc/passwd > sortedGroup.txt
````
> Save output of first command as a text in file called `sortedGroup.txt`


### Redirection

- Save text in a file (Override it's content)
````
echo arafat > fil1.txt
````

- Concatenate (append) text in a file (in new line) as `str = str+text` in programming
````
echo is my best friend >> file1.txt
````