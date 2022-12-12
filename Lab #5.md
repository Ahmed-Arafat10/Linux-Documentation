# OS2 : Lab #5
#### By TA `Ahmed Arafat` (>‿◠)✌
#### Special Thanks To My Wonderful Mate TA `Mohamed Khaled` 💕


### Users and Groups Administration :
- User account is a systematic approach to track and monitor the usage of system resources.
- Each user account contains two unique identifiers -> `username` & `UID`


### Types of users
- `Root user` -> `UID` is `0` [`Has All privilege`]
- `Regular user` -> `UID` >= `1000`
- `Service accounts` -> created when packages are installed `ex: network,audio,docker,etc` -> `0` < `UID` <= `999`


- Managing files and groups are done by these files:
    - `/etc/passwd` {contains `7 fields`} --- contains all configuration f system
    - `/etc/shadow` {contains `9 fields`} --- contains encrypted data of passwords in system
    - `/etc/group` {contains `4 fields`} --- `gname:password:GID:group_members`


- Add a user in system
```
sudo useradd arafat
```
> Rest values will be automatically allocated

OR
```
sudo useradd -u 1000 -g 2000 -c "Ahmed Arafat" -md /home/arafat -s /bin/bash arafat
```
- `-u` : `UID`
- `-g` : `GID`
- `-c` : `comment`
- `-md` : `Home Directory`
- `-s` : `shell`
- Then `username` (`arafat` in this command)


- To change password or assign a password for a user for the first time
```
sudo passwd <username>
```

- To switch to a specific user
```
su <username>
```
> you will then enter his password

- To go back to previous username enter `exit` OR `Ctrl + d`

- In Line #31, shadow has `9 fields` :
  - Username
  - Encrypted Password (One-way encryption)
  - Date when password was last changed
  - Number of days before password can be changed (minimum password age)
  - Number of days after password must be changed (maximum password age)
  - Number of days before password expiry date to display the warning
  - Number of days to disable account after password expire
  - Number of days since the account is disabled
  - Reserved field (Not commonly used)


- To display `shadow` field for a specific user
```
sudo chage -l <Username>
```
> `-l` : list fields

> Note : some commands need to have `sudo` at the beginning, this means that no one can perform such a command except the `root` user

- Some flags used with `chage`
    - `-l (small L)` -> view ageing information about account
    - `-d` -> change last password change date `-d 2021-12-31`
    - `-E` -> set when account expires `-E 2022-12-31`
    - `-M` [Max] OR `-m` [Min] -> changes password `max` or `min` age `-M 5`
    - `-w` -> Number of days to give prior warning before the password expires `-w 2`
    - `-l (capital i)` -> specify number of days account should be inactive after its expiry `-I 5`
- Example : 
``` 
sudo chage -m 5 -w 2 arafat
```



- Modify user's data
```
usermod -l arafat AhmedArafat
```
> -l : To change name of username
- Note : `usermod` uses same flags as `useradd`

- For a group you can have a : 
  - `Primary group` (Only one member) -> group's name is same as user's name
  - `Secondary group` (Many members) -> Any other group

- To create an empty group
````
sudo groupadd <GroupName>
````
> you can add `-g` -> `GID`

- To add a user to group
```
usermod -G <GrouoName> <Username>
```
- To remove a user
```
sudo userdel -r <UserName>
```
> `-r` : To remove his home Directory + mails

- To remove a group
``` 
sudo groupdel <GroupName>
```
- Edit group data
```
sudo groupmod -n zodiac Zodiacs -g 1001
```
> `-n` : To change name <br>
> `-g` : To change UID <br>


- `.password` file is a backup file for `password` file in path `/etc` as it is a critical file



## File Permission and Ownership :

- `-|rwx|r-x|--- 1 arafat Zodiacs 0 Oct 31 11:06 Test.txt`

- `-` --> file type [`-` > file while `d` -> Directory]
- `rwx` -> user permission
- `r-w` -> Group permission
- `---` -> other permission
- `1` --> # of `hard link` (will be discussed later)

>O/P:
- `ahmed` -> user owner
- `Zodiacs` -> group owner
- `0` -> file size
- `Oct 31 11:06` -> last modified time
- `Test.txt` -> name of file


- VIP Octa Numbers:
    - `r (Read)` = 4
    - `w (Write)` = 2
    - `x (Execute)` = 1


- Directory:
    - `r` for a Directory. -> to be able to perform command `ls` to this Directory (check files/directories in this file)
    - `w` for a Directory. -> to copy/create file/Dir. to/inside it
    - `x` for a Directory -> to be able to perform command `cd` this Directory (to be able to enter it)


- File:
    - `r` for file -> read its content
    - `w` for a file -> to edit its content
    - `x` for a file -> to execute executable files as `.cpp`/`.java`


- To show permission/ownership for a file
```
ls -l <FileName>
```
- To show permission/ownership for a Directory
```
ls -ld <DirName>
```

- To change permission of File/Directory
```
chmode <FileName>
```
Example:
```
chmod u=rwx, g=rw, o=r file.txt
```
OR
```
chmod 763 file.txt
```
   - `7` means `rwx` as `4+2+1` <br>
   - `6` means `rw` as `4+2` <br>
   - `3` means `wx` as `2+1` <br>

- Note : In `chmod` command :
  - `u-rw` -> remove from user `r,w` permissions (now `user = x`, assuming that he already has `x` permission)

> Note: Root user can `r`/`w`/`x` any file, if its permission is not allowed, as he has all privilege


- VIP Note:
    - To copy a file I have to have `r` permission
    - To copy a file to a Directory, Directory should have both `w`&`x` permissions
    - To copy a Directory to another Directory, copied Directory should have `r`&`x` permissions
      while Directory which will contain copied one should have `w`&`x` permissions
