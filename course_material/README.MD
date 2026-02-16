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
    1. The password entry won't show somthing being typed, but password
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

## Setting-up Git and GitHub

Once you have WSL, you can configure your local git with username and
email address and also choose the default text editor (eg. vim).

```
git config --global user.name “Abhin Suresh”
git config --global user.email user@users.noreply.github.com
git config --global core.editor vim
```

To clone the project GitHub repo using SSH method, you need to add SSH key to 
your GitHub account. To do that

01. From your terminal (WSL in windows): `ssh-keygen`.
    1. this will ask for the file in which to generate the key pair, 
    you can enter nothing and go with the default option.
    2. this also ask for a passphrase, you can also go with default empty option.
    3. This will generate a public key, private key pair in .ssh folder 
       in home directory (to go to home dir: `cd` or `cd $HOME`). 
       The public key ends with .pub file. 
02. You need to copy the public key (eg. `.ssh/id_rsa.pub`) to your
    GitHub account add SSH-KEY in settings
    ```
    GitHub profile icon > Settings > SSH and GPG keys > New SSH key
    ```
03. Now you can clone the repo using SSH
    1. Go to your corresponding repo from the https://github.com/NSF-DARSE/RSE-course
    2. In `<> Code` button choose SSH option, copy the command
    3. In your terminal enter `git clone <paste-git-repo>`
    4. Start a new branch `git switch -c feature_branch`
    5. Edit readme file to include project description
    6. Stage `git add <file>` and commit `git commit -m "message"`
    7. push changes to the repo also by adding upstream tracking branch
        `git push -u origin feature_branch`
