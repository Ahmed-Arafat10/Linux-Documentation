# Session #3



- Show all environment variables whether they are empty or not {In line #970}
```
man bash
```

- Show all environment variables that have values (not empty)
``` 
printen
```
OR
```
env
```


Users and Groups Administration :
-------------------------------
- User account is a systematic approach to track and monitor the usage of system resources.
Each user account contains two unique identifires -> username & UID


Types of users :
----------------

- Root user -> UID is 0 {Has All privilege }
- Regular user -> UID >= 1000
- Service accounts -> created when packages are installed {ex: network,audio,docker,... } -> 0 < UID <= 999


- Managing files and groups are done by those files:
    - /etc/passwd {7 fileds} --- contains all configuration f system
    - /etc/shadow {9 fields} --- contains encrypted data of passwords in system
    - /etc/group {4 fields} --- gname:password:GID:group_members


- Add a user in system
```
sudo useradd arafat
```
- Rest valus will be automatice allocated
OR
```
sudo useradd -u 1000 -g 2000 -c "Ahmed Arafat" -md /home/arafat -s /bin/bash arafat
```
- -u : UID
- -g : GID
- -c : comment
- -md : Home Directory
- -s : shell
- Then username {arafat in this command}


- To change password or assign a password for a user for the first time
```
sudo passwd <username>
```

- To switch to a specific user
```
su <username>
```
> you will then enter his password

- To go back to previous username
-> enter ```exit``` OR   ``` Ctrl + d ```


    - In Line #31, shadow has 9 fields :
        - Username
        - Encrypted Password {One-way encryption}
        - Number of days when password was last changed
        - Number of days before password can be changed (minimum password age)
        - Number of days after password must be changed (maximum password age)
        - Number of days before password expiry date to display the warning
        - Number of days to disable account after password expire
        - Number of days since the account is disabled
        - Reserved field {Not commonly used}


    - To display [shadow] field for a specific user
  ```
  sudo chage -l <Username>
  ```
  > -l : list fields

- Some flags used with ``` chage ``` 
    - l (small L) -> view ageing information about account
    - d -> change last password change date (-d 2021-12-31)
    - E -> set when account expires (-E 2022-12-31)
    - M {Max} {OR} m {Min} -> changes password max or min age {-M 5}
    - w -> Number of days to give prior warning before the password expires {-w 2}
    - l (capital i) -> specify number of days account should be inactive after its expiry {-I 5}
- Example: ``` sudo chage -m 5 -w 2 arafat ```



   - Modify a user data
   ```
   usermod -l arafat AhmedArafat
   ```
   > -l : To change name of username
   - Note : ```usermod``` uses same flags as ```useradd```

    - For group you can have a : 
        - Primary group (Only one) -> {your names group}
        - Secondary group (Many) -> {Any other group}


    - To create an empty group
  ```
  sudo groupadd <GroupName>
  ```
  > you can add [-g] -> GID


- To add a user to group
  ```
  usermod -G <GrouoName> <Username>
  ```
 - To remove a user
  ```
  sudo userdel -r <UserName>
  ```
  > -r : To remove his home Directory + mails

 - To remove a group
``` 
sudo groupdel <GroupName>
```
- Edit group data
```
sudo groupmod -n zodiac Zodiacs -g 1001
```
> -n : To change name <br>
> -g : To change UID <br>


- [.password] file is a backup file for [password] file in path [/etc] as it is a critical file



File Permission and Ownership :
------------------------------

 - User X is not in the sudoers file -> to fix this [/etc/sudoers]

 - vi sudo -> search for it in google 


 - -|rwx|r-x|--- 1 arafat Zodiacs 0 Oct 31 11:06 Test.txt

 - [-] --> file type {- -> file // d -> Dir.}
 - [rwx] -> user permission
- [r-w] -> Group permission
- [---] -> other permission
- [1] --> # of hard link (will discuss it in next sessions)

<br>

- ahmed -> user owner
- Zodiacs -> group owner
- 0 -> file size
- Oct 31 11:06 -> last modified time
- Test.txt -> name of file


- VIP Octa Numbers:  
    - r {Read} = 4
    - w {Write} = 2
    - x {Execute} = 1

- Directory:
    - [r] for Dir. -> to [ls] this Dir.
    - [w] for Dir. -> to copy/create file/Dir. inside it
    - [X] for Dir. -> to go to [cd] this Dir. {enter it}

- File:
    - [r] for Dir. -> read its content
    - [w] for Dir. -> to edit its content
    - [X] for Dir. -> to execute executable files as .py/.cpp


- To show permission/ownership for a file
```
ls -l <FileName>
```
- To show permission/ownership for a Directory
```
ls -ld <DirName>
```


- To change permission of file/Dir.
```
chmode <FileName>
```
Example:
```
chmod u=rwx,g=rw,o=r file.txt
```
OR
Example: 
```
chmod 764 file.txt
```
> r ->  7 -> 4+2+1 <br>
> w ->  6 -> 4+2 <br>
> x ->  4 -> 4 <br>

- Note : In [$ chmod] command  u-rw -> remove from user r,w permissions {now user = x, assuming that he already has x}

- Note: Root user can [r/w/x] any file, if its permission is not allowed, as he has all privilege

- Note: you cannot prevent a user from deleting a file even if it has [---], but there is a way to protect it using the
Dir. it exist in

- VIP:
    - To copy a file I have to have [r] permission
    - To copy a file to a Dir. , Dir. should have [w][x] permission
    - To copy a Dir. to another Dir. , copied Dir. should have [r][x] permission
    while Dir. which will contain copied one should have [w][x] permission



Initialization Files :
---------------------

- ``` ~/.bashrc``` OR ```~/.bash_profile```: are local files for each user so, environment variables
will be shown only for one user

- ```/etc/profile``` OR ```/etc/bashrc``` OR ```/etc/bash.bashrc``` {Global files} : if you put inside it an
    environment variable, it will affect all users in system



Linux Package Manager (apt) : Just goole program you want to download
--------------------------

```
sudo apt policy git
```

```
sudo apt update
```

```
sudo apt upgrade
```

```
wget
```

```
docker --version
```

```
docker -compose
```
