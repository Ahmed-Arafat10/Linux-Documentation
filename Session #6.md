# Session #6 :


- Testing and Logical operations:
    -a                  : and operator <br>
    -o                  : or operator <br>
    -f <FileName>       : File Existence {1:false , 0:true} <br>
    -h <FileName>       : symbolic Link <br>
    -r <FileName>       : Readable <br>
    -w <FileName>       : Writable <br> 
    -x <FileName>       : Executable <br>

- String Testing:
    - ```str1 = str2```
    - ```str1 != str2```
    -  ``` -2 string```
    -  ``` n string```

- Integer Testing:

    - ``` int1 -eq intr2 ``` {==}
    - ``` int1 -ne intr2 ```{!=}
    - ``` int1 -gt intr2 ``` {>}
    - ``` int1 -lt intr2 ```{<}
    - ``` int1 -ge intr2 ```{>=}
    - ``` int1 -le intr2 ``` {<=}


If Command:
-----------
 ```  
    if command
    then
        -command
    fi
```                                 
OR
```
    if [expression]
    then
        -command
    fi
```
- Nested If Command:
```
if command
then
    -command
    if command
    then
        -command
    fi
fi
```
In file.sh :
 ```
echo "Enter Your age"
read
echo "Your age is $REPLY"
```
OR
                                 
 ```                        
    echo "Enter Your age"
    read answer
    echo "Your age is $answer"
```
OR
- You can use ```$1``` and pass input as an argument without having to use read


Case :
-----
```                         
case variable in
  Value1) command(s)
    ;;
  Value2) command(s)
    ;;
  *) command(s)
   ;;
esac
```
                         
While :
------

```                         
    while command
    do
        -command
    done
```
EX:
```                         
    num=0
    while [$num -it 10]
    do
        echo $num
        let num=$num+1
    done
```
VIP Note: If you want to calculate a text with a string use this method
```
    str=ahmed
    str="$str"arafat
    echo $str
    O/P : ahmedarafat
```

Until :
------
```
     until command
     do
        -command
     done
```
Note: for ```until```, while condition is false you will enter loop when it become true
you will exit from it


For :
----
```
    for variable in word list
    do
        -command
    done
```
Select:
-------

 Example:
```
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
```
- Note : To exit write [exit] or break
- ```exit``` will terminate whole script like return 0 in C Language

> ``` break ``` <br>
> ``` continue ```

Shift:
------

In File.sh :
```
    echo $1
    echo $2
    echo $3
    shift 2
    echo "----------------"
    echo $1
    echo $2
    echo $3
 ```
-> It shift (Add) 2 to parameter in echo statements after it
```$1``` become ```$3```
```$2``` become ```$4```
and so on

-Run command {```source script.sh 1 2 3 4 5```}
```
O/P :   1
        2
        3
        -----------
        3
        4
        5
```
Arrays:
-------

- Bash supports numerically=y indexed and associative arrays types {Using intergers or strings}
- You can delete an index (element)

- Initialize an index
```
    array[0]=ahmed
```
- Initialize a whole array
```
    arr = (Element1 Element2 ElementN)
```
- Add new elements to an array
```
    arr += (NewElement1 NewElement2 NewElementN)
```
- Delete an element
```
    unset arr[index]
```
- Print an index
```
    echo ${arr[index]}
```
- Display all elements of an array
```
echo ${arr[*]}
echo ${arr[@]}
for i in "${arr[@]}"
do
    echo "$i"
done
echo ${#arr[@]}
```

Cron Job :
----------

- Use ```crontab -e ``` command <br>
Syntax : ``` 1 2 3 4 5 <ScriptFullPath> arg1 arg2 ``` <br>
where : 1-> Minute {0-59} <br>
        2-> Hours {0-23} <br>
        3-> Day {0-31} <br>
        4-> Month {0-12 [12 == December]} <br>
        5-> Days of weak (0-7 [7 OR 0 == sunday]) <br>

Example :   
    ```
    0 22 * * 1 ~/myscipt.sh
    ```
- This Means that device will run this script every Monday at 10 : 00 pm

- ``` cron -e ``` -> will open file in /temp/.../crontab, where you can put command in it
```
    crontab -l
```
- Make sure crin service is running
```
    service crone start
```
- Run crin tab every minute
```
    * * * * * /home/ahmed/for.sh
```
*/5 -> to run every 5 minutes
> You have to enter full path of script

- to make a cron tab for specific user
```
    crontab -e -u <User>
```
