### Adjust Your Screen Resolution
````shell
xrandr --output DVI-I-0 --mode 1368x768
````

### Turn On Keyboard Light
````shell
xset led
````

### To Check If Nvidia Driver Is Installed Or Not
````shell
nvidia-smi
````

### Install CodeBlocks Compiler
````shell
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install g++
````


### make Change Permanent
- create a script file then add both `xrndr` then `xset`.
- open `Startup application` then add new Config, name it then add
- bash `<ScriptPath>` in Command




### Give Access to a folder for PHP
````shell
sudo chown arafat -R /opt/lampp/htdocs/To-Do-List-E-Commerce/
````

### Open a folder from Terminal
````shell
nautilus <FolderName>
````