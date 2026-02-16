## Setting-up WSL in windows

Windows Subsubsystem for linux (WSL) is a Linux virtual machine that can
be installed in your windows operating system. Assuming you don't already
have WSL in your system, to install WSL in windows you need to enable 
some windows features.

```text
Control Panel > Programs > Turn Windows features on or off
```

Contents in the pop-up new window might take a while to load. In that 
windows check boxes for Virtual Machine Platform and Windows Subsystem
for Linux. Then, windows will fetch required files and you will have 
to restart the device to have it enabled in your system.

Now, go to Microsoft Store (if not installed as a program in your device, 
go to Microsoft Store in a browser) and search for Ubuntu 24.04 to install
the WSL virtual machine.

Once installed

01. Open the Ubuntu 24.04 app 
02. The App will do some intialization installation for few minutes...
03. It will ask for your UNIX username and password
    a1. the password block won't show somthing being typed, but password
        is being recorded, just enter your password and press enter. You
        also have to enter it twice for verification
04. Before running any other commands it reccomended to do update the 
    UNIX system through the command.  
    `user@pc:$ sudo apt update && sudo apt upgrade -y`

Now you have Linux system to work with, it comes with Python3.1X and 
corresponding pip package mangement system. Once the system update is 
complete, you should also have access to the built-in venv module, 
which allows you to create isolated Python virtual environments for 
your projects.

You can also upgrade the pip, using the command

```
python3 -m pip install --upgrade pip
```
 
