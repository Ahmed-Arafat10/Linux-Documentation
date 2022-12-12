# OS2 : Lab #7 - Bash Script
#### By TA `Ahmed Arafat`

### Let's start with dealing with bash script files
- First create a file with extension `.sh`
````shell
nano script1.sh
````
- Then type inside it :
```shell
echo "script is $0"
echo "Number of arguments are $#"
echo "List arguments $*"
echo "Argument 1 = $1"
```
- Let's see meaning of each sign :
  - `$#` > Number of argument  <br>
  - `$*` > list all arguments  <br>
  - `$1,$2,etc` > first, second argument  <br>
  - `$0` > script name  <br>

- To run a `bash script`
````shell
./script.sh arg1 arg2 arg3
````
- The output will be :
```shell
script.sh
3
arg1 arg2 arg3
arg1
```

- Now let's see dealing with `variables` in `terminal` or in `scripts`
````shell
i=5                      
echo $i
````
> Output: 5
````shell
i=$i+1 
echo $i
````
> Output: '5+1'
- to make a summation not concatenation operation
````shell
let i=$i+2
echo $i
````
> Output: 7

- Or you can specify the `data type` of the `variable`
````shell
typeset -i Num
Num=5
echo $Num
Num=$Num+5
echo $Num
````
> Output: `5` then `10`

### To speficiy that this file is a script file type in the header of the file
````shell
#! /bin/bash
````
> This line is called `sh-bang` or `hashbang`

### Logical Operators:

 - `-a` means `and` operator
 - `-o` means `or` operator
 - `-f <FileName>` means File Existence (`1`:true , `0`:false) 
 - `-h <FileName>` means symbolic Link
 - `-r <FileName>` means Readable
 - `-w <FileName>` means Writable
 - `-x <FileName>` means Executable
<br>

- `String` Comparison :
  - `str1 = str2`
  - `str1 != str2`
  - `-2 string`
  - ` n string`

- `Integer` Comparison :

    - `int1 -eq intr2` means `==`
    - `int1 -ne int2` means `!=`
    - `int1 -gt intr2` means `>`
    - `int1 -lt intr2` means `<`
    - `int1 -ge intr2` means `>=`
    - `int1 -le intr2` means `<=`


## `If` Statement :
````shell
if [expression]
then
     -command
fi
````
### Nested `If` Statements :
````shell
if command
then
    -command
    if command
    then
        -command
    fi
fi
````

## Read an Input :
- In `script.sh` type :
````shell
echo "Enter Your age"
read
echo "Your age is $REPLY"
````
> `$REPLY` is a variable created from line `read`

`OR` you can create your own variable
````shell                        
echo "Enter Your age"
read answer
echo "Your age is $answer"
````
> you have created `answer` variable

> `OR` You can use `$1` and pass input as an `argument` without having to use `read`


## `Case` Statement :
````shell                     
case variable in
  Value1) command(s)
    ;;
  Value2) command(s)
    ;;
  *) command(s)
    ;;
esac
````

## `While` Statement:

````shell                         
while [ command ]
do
    -command
done
````
> Example, create a `while` loop to print from `0` to `10`
````shell                         
num=0
while [$num -le 10]
do
    echo $num
    let num=$num+1
done
````

### `Concatenate` a text with a `string` :
````shell
str=ahmed
str="$str"arafat
echo $str
````
> Output : ahmedarafat

## `Until` Statement:

````shell
until [ command ]
do
   -command
done
````
> Note: for `until`, while condition is `false` you will execute the loop when it becomes `true`
you will exit from it


## Select Statement :

- `select` is used then you want to create a menu for the user
Example:
````shell
select choice in Ahmed Mohamed Yousry
   do
      case $choice in
         Ahmed) print "Ahmed"
          ;;
         Mohamed) print "Mohamed"
          ;;
         Yousry) print "Yousry"
          ;;
         *) print "$reply is not one of the choices"
          ;;
      esac
   done
````
> Note : To exit write `exit` or `break`
- `exit` will terminate whole script like `return 0` in `C Language`

### To run a `script`
````shell
source Script.sh
````
Or
````shell
./Script.sh
````
> Also don't forget to add `execute` permission to bash script file
````shell
chmod 777 script.sh
````

<hr>
<hr>
<hr>

## Let's See More Examples On `Bash Script`

### 1. `script1.sh`, `Bash Script For Arguments`
````shell
  echo "Script name is $0"
  echo "Num of arguments are $#"
  echo "list arguments $*"
  echo "argument 1 = $1"
````


### 2. `script2.sh`, `Bash Script For Inputs`
````shell
echo "Enter Your age"
read answer
echo "Your age is $answer"
````


### 3. `script3.sh`, `Bash Script For While Loop`
````shell
#! /bin/bash
num=0
while [ $num -lt 10 ]
do
    echo $num
    let num=$num+1
done
````

### 4. `script4.sh`, `Bash Script For While Loop & If Statement`
````shell
#! /bin/bash
num=0
while [ $num -lt 10 ]
do
    echo $num
    if [ $num -eq 5 ]
    then
        echo "ferial"
    fi
    let num=$num+1
done
````

### 5. `script5.sh`, `Bash Script For String Concatination`
````shell
echo "please enter two stings to concatenate them"
read str1
read str2
echo "$str1" $str2
````

### 6. `script6.sh`, `Bash Script For Calculating Factorial`
````shell
#! /bin/bash
typeset -i num=$1
typeset -i i=1
typeset -i fact=1
while [ $i -le $num ]
do
    fact=$fact*$i
    i=$i+1
done
echo "Factorial of number $num is $fact"
````


### 7. `script7.sh`, `Bash Script For Case Statement`
````shell
#! /bin/bash
echo "please enter first number"
read num1
echo "please enter second number"
read num2
echo "please enter sign"
read sign
typeset -i res
case $sign in
  +)
  res=num1+num2
  ;;
  *) echo "error"
  exit
  ;;
esac

echo "result is $res"
````

### 8. `script8.sh`, `Bash Script For Select Statement`
````shell
#! /bin/bash
select choice in bis cic auc guc
do
case $choice in
bis) echo "your college is bis" ;;
cic) echo "your college is cic" ;;
auc) echo "your college is auc" ;;
guc) echo "your college is guc" ;;
*) echo "not in the list"
exit
;;
esac
done
fi
````

### 9. `script9.sh`, `Bash Script For If Statement & AND Operator`
````shell
#! /bin/bash
n1=$1
n2=$2
if [ $n1 = "ahmed" -a $n2 = "arafat" ]
then
  echo "hello TA"
fi
````
