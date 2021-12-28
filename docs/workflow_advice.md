# Workflow Advice

General advice on sundry topics such as working in the shell.

## Working in the Shell

### Create a code or projects workspace

When first learning the bash command line, it's helpful to organize projects in a single place.

Open a shell and type the following to create a `code/` directory. 

```
#to create the directory in your home directory
mkdir ~/code

#to create the directory in your Desktop
mkdir ~/Desktop/code
```

Better yet, create a new folder in the `code` directory and work inside of that.

```
cd ~/Desktop/code
mkdir new-project
cd new-project
```

If you're ever confused about which directory you're in on the command line, type `pwd` to print the "working" directory. If you want to see the files contained within a directory type `ls` to print the folders and files and `ls -a` to print all folders and files including hidden ones.

### Tinker in shell, copy to code editor

If you're working on a [shell script](http://swcarpentry.github.io/shell-novice/06-script/index.html) that requires multiple commands (e.g. creating a script that downloads and processes data), a common workflow is to start by experimenting with the commands directly in the shell.

Once you're confident that a command is working as expected, copy and paste the command over to the script.

Remember, you should be using a proper code editor such as Visual Studio Code to create and edit shell scripts.

### Recovering "lost" commands

You can easily review a history of commands you've typed on a shell by invoking the [history](https://www.rootusers.com/17-bash-history-command-examples-in-linux/) command.

```
history
```

If you're trying to pinpoint certain commands, you can also filter the list returned by `history`:

```
# Example searching for commands that operated on CSVs
history | grep csv
```

## Python

### Interactive shell

Python ships with an interactive interpreter that you can fire up from any shell terminal by simply typing `python`. This interactive environment allows you to test out Python code in a live environment. It's incredibly useful for experimenting with code prior to moving into a longer script (similar to the workflow described above for tinkering on the shell).

We recommend installing [ipython](https://ipython.readthedocs.io/en/stable/), a more user-friendly and feature-rich version of the Python interactive interpreter.

```
pip install ipython
```

Now fire it up.

```
ipython
```

Once you're done working, exit the Python interpreter and return to the regular bash shell:

```
# Either type `CTRL + d` or
exit()
```

