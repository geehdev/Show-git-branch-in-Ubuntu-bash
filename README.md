# Hello, welcome everyone! 👋

*First we have to understand that there are two types of shells, the default shell that the system usually uses is called the non-login shell, when using it the user is asked for the password when trying to install a program through its package manager. The login shell is the opposite of this, it doesn't ask for your password and you can install it without interference from the system, you can access it using the "sudo su" command, but we won't use it.*

*In this tutorial you will learn how to show the name of your current git branch in your shell without login, bash, terminal, you choose what to call it... This will optimize your time by making it explicitly visible 🤩*

## Showing git branch in your shell 🐙
>**Step 01** *(Open your terminal and type the command below) 👇🏽*

`sudo chmod -R 777 ~/.bashrc`

*If the ".bashrc" file does not exist, you must use the command below 👇🏽*

`sudo chmod -R 777 ~/.bash_profile`

*This command will allow you to make changes to the above file, you will be asked for your user password and nothing will be returned.*

>**STEP 02** (Basic mode) 🌲

*After performing STEP 01, you must type the following command 👇🏽*

`gedit ~/.bashrc`

**OR**

`gedit ~/.bash_profile`

*This command is a really cool shortcut, it will open the file we are going to modify directly in the gedit text editor*

**Comments:**
*If your system does not have gedit installed by default, try replacing the name "gedit" with "kate" or the name of your text editor.*

> **STEP 03** (Basic mode) 🌲

*After opening the ".bashrc" or ".bash_profile" file, scroll to the end of the file and paste the following command*👇🏽

```
# show branch name in prompt (branch)
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# show branch name in prompt (branch)
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\[\033[01;33m\]$(parse_git_branch)\[\033[01;00m\] $ '
```
## Customize your branch output 🎨
*You may have noticed that your branch name is in yellow, the reason for this is this little bit "[\033[01;32m\]" in the code above! You can modify these digits to change their color and more.*

*Get new digits here >>* [**Bash-Colors**](https://gist.github.com/JBlond/2fea43a3049b38287e5e9cefc87b2124)


*To finish, save your file with the modifications above, check it in your shell, use the "cd" command to navigate to a git repository, branches normally only appear after the first commit. Make a commit and your branch name should appear in your shell.*


**END OF TUTORIAL!** 🥳 \ *Below you will see a second way to do the same process.*



> **STEP 02** (Advanced Mode) 🌵
*Here we will use nano, it is a simple text editor via shell, that is, we will do STEP 03 without leaving the shell.*

*After performing STEP 01, you must type the following command in your shell 👇🏽*

`nano ~/.bashrc`

**OR**

`nano ~/.bash_profile`

*This command will open the file that we will modify directly in your shell.*

> **STEP 03** (Advanced Mode) 🌲
*After opening the ".bashrc" or ".bash_profile" file using nano editor, scroll to the end of the file and paste the same code 👇🏽

```
# show branch name in prompt (branch)
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# show branch name in prompt (branch)
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\[\033[01;33m\]$(parse_git_branch)\[\033[01;00m\] $ '
```

*To finish, save the changes by pressing the "Ctrl + S" keys, then press the "Ctrl + X" keys to close nano and return to the previous shell.*

**END OF TUTORIAL! Until next time...**