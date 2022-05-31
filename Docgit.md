# Activate ssh to sign commits in Mac and Windows

-----

## About 
## How to install in Mac

1. Install HomeBrew 
In your terminal run the next command
```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
* While the installation is running that required a enter and then your system password

* You can check if brew installation was sucessfully running 
```
    brew help
```
* Note: If the terminal response is zsh: command not found: brew , you have to run again the brew install

2. Install Git 
``` 
    brew install git
```
* You can check if git installation was sucessfully running 
```
    git version
```
* Note: If the terminal response is zsh: command not found: git , you have to run again the git install 

3. In GitHub WebPage, go to your presonal settings -> access -> emails. In this step add your corporative email. 

4. in your terminal run the next commands with your name and email to configure your global variables.
```
    git config --global user.name "Your Name"
    git config --global user.email Your@email.com
```
* Remember only use your corporative email to sign yours commits
* Note: Check yours parameters with the next line
    `````
        git config --list
    ````

5. Run SSH command to generate de .pub key
````
    ssh-keygen -t rsa -b 4096 -C "Your@email.com"
````
* During this command terminal required a file destination, that could be in default (~/.ssh/) so only click enter, then you have to type a passphrase and finally the terminal show as the key and the file name

6. Then we have to create a file called config in the folder where you put your .pub key
````
    touch ~/.ssh/config
    vim ~/.ssh/config  
````

7. Type the next lines into the config file
````
    Host *
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ~/.ssh/id_rsa 
````
* Note: Check the .pub name, to default is called id_rsa, but maybe it's different

8. Add the private key to the ssh-agent
````
    ssh-add -K ~/.ssh/id_rsa
````

9. Then use the pbcopy comand to copy in your clipboard 
````
    pbcopy < ~/.ssh/id_rsa.pub
````

10. In GitHub WebPage, go to your presonal settings -> access -> SSH and GPG keys -> New SSH Key. In this step type a title like "MacBook Yape" and paste your key. 