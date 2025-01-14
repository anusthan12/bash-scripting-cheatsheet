`Note: These notes are for my personal reference!`

# 𝐁𝐚𝐬𝐡 𝐒𝐜𝐫𝐢𝐩𝐭𝐢𝐧𝐠 𝐂𝐡𝐞𝐚𝐭𝐬𝐡𝐞𝐞𝐭

## 𝐁𝐚𝐬𝐢𝐜𝐬

- Telling interpreter that the file is bash file

```
!#/bin/bash
```

- Make the file executable
```
$ chmod +x script.sh
```

## 𝐂𝐨𝐦𝐦𝐞𝐧𝐭𝐬

```
# this is a single line comment 
```
```
# Multi line comment

# - Method I
<<COMMENTS
  This 
  is a 
  multiline
  comment
COMMENTS

```
```

# - Method II
:'
 This 
  is a 
  multiline
  comment
'

```

## 𝐕𝐚𝐫𝐢𝐚𝐛𝐥𝐞𝐬

- Syntax: `variable_name=variable_value`
- `Note: There should not be any white spaces on either side of the =`
- `Single quotes (') helps to treat every character as it is`
- `Double quotes (") helps to do the substitution`

---

System Defined Variables | Meaning
--- | ---
`BASH` | represents the Shell Name.
`BASH_VERSION` | specifies the shell version which the Bash holds.
`COLUMNS` | specify the no. of columns for our screen
`HOME` | specifies the home directory for the user
`LOGNAME` | specifies the logging user name.
`OSTYPE` | tells the type of OS.
`PWD` | represents the current working directory.
`USERNAME` | specifies the name of currently logged in user.

```
                                                                                      
#!/bin/bash

echo $BASH
echo $BASH_VERSION
echo $COLUMNS
echo $HOME
echo $LOGNAME
echo $OSTYPE
echo $PWD
echo $USERNAME
                                                                                       
```

---

## 𝐑𝐞𝐚𝐝𝐢𝐧𝐠 𝐈𝐧𝐩𝐮𝐭

- Syntax: `read [flag] varname`
  - `-s` : for silent mode
  - `-p` : for prompt mode
  - `-a` : for arrays

```
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ cat read.sh  
#!/bin/bash

echo "firstname: "
read firstname
echo "lastname: "
read lastname

echo "Hello Mr. $firstname $lastname"

┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ ./read.sh  
firstname: 
shreyas
lastname: 
chavhan
Hello Mr. shreyas chavhan

```


```
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ vim read_prompt.sh
                                                                                       
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ chmod +x read_prompt.sh 
                                                                                       
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ cat read_prompt.sh     
#!/bin/bash

read -p "Your Name: " name

echo "Hello Mr. $name"
                                                                                       
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ ./read_prompt.sh 
Your Name: Shreyas
Hello Mr. Shreyas
                          
```
```
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ vim read_silent.sh
                                                                                       
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ ./read_silent.sh  
Your Password 
Your Password is mypassword, it's secret - don't tell anyone!
                                                                                       
┌──(shreyas㉿kali)-[~/practise/bash_scripting]
└─$ cat read_silent.sh 
#!/bin/bash


read -sp "Your Password " password

echo ""
echo "Your Password is $password, it's secret - don't tell anyone!"

```

- Multi-line input

```
while read -r line; do
   printf '%s\n' "$line"
done
```

---


## 𝐁𝐚𝐬𝐡 𝐢𝐟-𝐞𝐥𝐢𝐟-𝐞𝐥𝐬𝐞


- Syntax
```
if [condition]; then
  <blah blah>
elif [condition]; then
  <blah blah>
else
  <blah blah>
fi

```


- `||` : OR
- `&&` : AND

Operators | Description
--- | ---
`! EXPRESSION` | To check if `EXPRESSION` is false.
`-n STRING` | To check if the length of `STRING` is greater than zero.
`-z STRING` | To check if the length of `STRING` is zero (i.e., it is empty)
`STRING1 == STRING2` | To check if `STRING1` is equal to `STRING2`.
`STRING1 != STRING2` | To check if `STRING1` is not equal to `STRING2`.
`INTEGER1 -eq INTEGER2` | To check if `INTEGER1` is numerically equal to `INTEGER2`.
`INTEGER1 -gt INTEGER2` | To check if `INTEGER1` is numerically greater than `INTEGER2`.
`INTEGER1 -lt INTEGER2` | To check if `INTEGER1` is numerically less than `INTEGER2`.
`-d FILE` | To check if `FILE` exists and it is a directory.
`-e FILE` | To check if `FILE` exists.
`-r FILE` | To check if `FILE` exists and the read permission is granted.
`-s FILE` | To check if `FILE` exists and its size is greater than zero (which means that it is not empty).
`-w FILE` | To check if `FILE` exists and the write permission is granted.
`x FILE` | To check if `FILE` exists and the execute permission is granted.

---

## 𝐁𝐚𝐬𝐡 𝐂𝐚𝐬𝐞𝐬

- Syntax:
```
#!/bin/bash  
  
echo "Which Operating System are you using?"  
echo "Windows, Android, Chrome, Linux, Others?"  
read -p "Type your OS Name:" OS  
  
case $OS in  
    Windows|windows)  
        echo "That's common. You should try something new."  
        echo  
        ;;  
    Android|android)  
        echo "This is my favorite. It has lots of applications."  
        echo  
        ;;  
    Chrome|chrome)  
        echo "Cool!!! It's for pro users. Amazing Choice."  
        echo  
        ;;  
    Linux|linux)  
        echo "You might be serious about security!!"  
        echo  
        ;;  
    *)  
        echo "Sounds interesting. I will try that."  
        echo  
        ;;  
esac  
```

---

## 𝐁𝐚𝐬𝐡 𝐟𝐨𝐫 𝐋𝐨𝐨𝐩

- C++ like for loop

```
for ((i = 0 ; i < 100 ; i++)); do
  echo $i
done
```

- To read a range
```
for num in {1..10}  
  do  
  echo $num  
done  
```

- a range with increment

```
for num in {1..10..1}  
  do  
  echo $num  
done  
```

- a range with decrement

```
for num in {10..0..1}  
  do  
  echo $num  
done  
```

- Array variables

```
array=(  "element1" "element 2" .  .  "elementN" )  
  
for i in "${arr[@]}"  
  do  
  echo $i  
done  
```

- white spaces in String as word separators

```
#!/bin/bash  
  
for word in $str;  
do  
  <Statements>  
done  
```

- Each line in string as a word

```
#!/bin/bash  
  
for word in "$str";  
  do  
  <Statements>  
done  
```

- Infinite loop

```
i=1;  
for (( ; ; ))  
  do  
  sleep 1s  
  echo "Current Number: $((i++))"  
done  
```
---

## 𝐁𝐚𝐬𝐡 𝐰𝐡𝐢𝐥𝐞 𝐥𝐨𝐨𝐩

- C++ Style while loop
```
i=1  
while((i <= 10))  
  do  
  echo $i  
  let i++  
done  
```



## 𝐎𝐭𝐡𝐞𝐫 𝐍𝐨𝐭𝐞𝐬

- Chop off the arithmetic operations to decimal points: `bc <<< "scale=3; $expression"` 
- Round of the arithmetic operation result: `printf %.3f $(echo $expression | bc -l)`
---
> Done
