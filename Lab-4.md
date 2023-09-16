## OS2 : Lab #4
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕

# VI Editor:

- Only editor available in rescue mode (as safe mode in windows)

```
vi file.txt
```

- hit `i` button to enter `insert mode`
- hit `esc` button to enter `command mode`

- In command mode:
    - `:q!` -> to Quit
    - `:wq!` -> to Write and then quite
    - `:w!` -> to Write (save)
    - You can use `up`/`down`/`right`/`left` buttons in `command mode`

- Also In command mode:
    - hit `yy` : to copy a line
    - hit `dd` : to cut a line
    - hit `p` OR `P` : to paste copied line, small `p` to put copied line under cur line and upper `P` to put it above
    - hit `D` -> Delete a line (from cursor to end of line)  `H[e]llo wolrd -> H`
    - `:n,nd` -> Delete Range of lines
    - `:%d` -> Delete all lines
    - `/text` -> to highlight text in file
    - hit `enter` then `n` button to go down or `N` button to go up to traverse along highlighted text
    - `:set nu` -> To show number of lines
```
1
2
3
```
- `:set nonu` -> to hide number of lines


## Environment Variables
```
x=arafat
echo $x
```
> O/P: arafat

```
echo $PWD
```
> O/P: `/home/arafat/Document`
```
echo $USER
```
O/P: `arafat`
```
echo $SHELL
```
> O/P: `/bin/bash`


- Export is used to create environment variables, best practices is to name it with upper case like this
```` 
export PP="/opt/lampp/htdocs"
````

Print the value stored in an environment variable
````
echo $PP
````
OR
````
printev PP
````
> no need to `$` sign

> Note: this is only for current terminal `not permanent`, 
to solve this save it in initialization files `~/.bashrc`


````
nano ~/.bashrc
````
> now we are editing `.bashrc` file

- To execute it or just close all terminals 
(as you are reloading page in web so changes can take place)
````
source ~/.bashrc
````
- To print all environment variables
````
printenv
````
OR
````
env
````

- To remove an environmental variable
```
unset <VariableName>
```
Example:
```
unset CURRENT_USER
```

# Command Quoting

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
> Will print `$PWD` as a text <br>
> `single quote` ignores all meta-character
```
echo '\$PWD'
```
> Will print `\$PWD` as a text
```
echo "\$PWD"
```
> Will print `$PWD` as a text <br>
> `Backslash` ignores next meta-character in `Double quotes`

````
history
````

- All commands written by you is saved in `~\.bash.history`
  - `!!` -> execute previous command
  - `!n` -> Example: `!350` -> execute command No. 350 in history
  - `!-n`-> Example: `!-2` -> previous previous Command `n Times`
