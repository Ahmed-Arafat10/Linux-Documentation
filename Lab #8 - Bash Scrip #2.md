# OS2 : Lab #8 (Final Lab) - Bash Script #2
#### By TA `Ahmed Arafat`

### `for` loop 
````shell
for(( i=0;i<100;i++ )) 
do   
  echo $i
done      
````
Or
````shell
for variable in word list
 do
    -command
  one
````

## Arrays:

- `Bash Script` supports `numerically indexed` and `associative arrays` types (Using integers or strings as an `Index`)

### 1. `numerically indexed` Array

- Initialize an index
````shell
array[0]=arafat
````

- Initialize a whole `array`
````shell
arr=("Apple" "Banana" "Cherry")
````

- Add new elements to an existing `array`
````shell
arr+=("Orange")
````

- Delete an element in an `array`
````shell
unset arr[3]
````

- Print an index 
````shell
echo ${arr[0]}
````
> Output: `Apple`


### 2. `associative` Array

- Initialize an associative `array`
````shell
declare -A arr1=( ["EGY"]="Egypt" [JPN]=JAPAN
[KOR]=Korea ["TWN"]="Taiwan cap" [TH]=Thailand )
echo ${arr1[JPN]}
echo ${arr1["TWN"]}
````

- Display all elements of an array
````shell
echo ${arr[*]}
# Or
echo ${arr[@]}
````

- Iterate on array's elements
````shell
for i in "${arr[@]}"
do
  echo "$i"
done
````

- Display size of the `array`
````shell
echo ${#arr[@]}
````

- Display all indices of the array
````shell
echo ${!arr[*]}
````


## More Examples On Bash Script

### 1. `script1.sh`
````shell
#! /bin/bash
read c
case $c in
  [a-z] ) echo "Lower case" ;;
  [A-Z] ) echo "Upper case" ;;
  [0-9] ) echo "Integer" ;;
  *) echo "None";
esac
````


### 2. `script2.sh`
````shell
#! /bin/bash

File=$(find /home/ubuntu/Lab8 -type f)

for CurFile in $File
do
        chmod u-x $CurFile
        echo "$CurFile has been modified"
done
````




### 3. `script3.sh`
````shell
#! /bin/bash
mkdir BackUp
File=$(find /home/ubuntu/Lab8 -type f 2> /home/ubuntu/Lab8/view_error)

for CurrentFile in $File
do
        cp  $CurrentFile ./BackUp
        echo "$CurrentFile has been coped to BackUp Directory"
done
````


### 4. `script4.sh`
````shell
#! /bin/bash
echo "How Many Elements You Want To Enter In An Array"
typeset -i num
read num
for(( i=0;i<num;i++ ))
do
        let n=$i+1
        echo "Please Enter Element No. $n"
        read Element
        arr[$i]=$Element
done
for(( i=0;i<num;i++ ))
do
        echo "The Element No. $i is -> ${arr[i]}"
done
````


### 5. `script5.sh`
````shell
#! /bin/bash
echo "How Many Elements You Want To Enter In An Array"
typeset -i num
typeset -i AV
typeset -i Sum=0
read num
for(( i=0;i<num;i++ ))
do
        echo "Please Enter Element No. $i"
        read Element
        arr[$i]=$Element
        Sum=Sum+${arr[$i]}
        echo $Sum
done
        AV=$Sum/$num
        echo "Average is : $AV"
````  

### 6. `script6.sh`
````shell
#!/bin/bash
echo "Enter the name of a month."
read month
case $month in
  February)
echo "There are 28/29 days in $month.";;
  April | June | September | November)
echo "There are 30 days in $month.";;
  January | March | May | July | August | October | December)
echo "There are 31 days in $month.";;
  *) echo "Unknown month. Please check if you entered the correct month name: $month";;
esac
````  




### 7. `script7.sh`
````shell
#! /bin/bash
echo "Please Enter A Number"
read num
if [ $num -gt 100 ]
then
echo "$num is larger than 100"
elif [ $num -gt 10 -a $num -le 100 ]
then
echo "$num is between 10 and 100 "
else
echo "number is less than 10"
fi
````  


### 7. `script7.sh`
````shell
#! /bin/bash
echo "Please Enter A Number"
read num
if [ $num -gt 100 ]
then
echo "$num is larger than 100"
elif [ $num -gt 10 -a $num -le 100 ]
then
echo "$num is between 10 and 100 "
else
echo "number is less than 10"
fi
````

### 8. `script8.sh`
````shell
#! /bin/bash
echo "Are You OK, Arafat ?"
read ans
if [ $ans = "y" -o $ans = "Y" ]
then
echo "Glad To Hear That ^-^"
else
echo "Nani !!!"
fi
````
