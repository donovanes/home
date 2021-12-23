# Technical Setup (Software, tools, etc.)

> See the [Technical FAQ page](tech_faq.md) if you run into snags and/or [report an issue](/issues).

- [Services and platforms](#services-and-platforms)
- [Windows](#windows-users)
- [Text Editor](#text-editor)
- [Shell terminal](#shell-terminal)
- [Version control](#version-control)
- [Python](#python)
- [Configure via script](#configure)
- [DataKit](#datakit)

## Services and Platforms

* Get the CPI [GitHub](https://github.com/) log in by emailing datascience@cpiglobal.org

## Windows users

Windows users will need access to a Linux system.

### Setting up the Virtual Machine (VM)
You will probably need to contact CTD (helpdesk@ctd.tech) if your work laptop is on the CPI domain to get started. 

* [Download](https://www.virtualbox.org/wiki/Download_Old_Builds_6_1) and [install](docs/virtualbox_setup.md) VirtualBox.
  
  VirtualBox version 6.1.28 has a bug when running on Windows 10 while Hyper-V is enabled. use 6.1.26 and matching extension pack in the link above. 
  
  **See here the [set up instructions for VirtualBox](docs/virtualbox_setup.md)**

* [Download](https://ubuntu.com/download/desktop) and [install](docs/ubuntu_setup.md) the Ubuntu virtual machine.
  It is recommended to download the 20.04.3 LTS version
  
  **See here the [set up instructions for the Ubuntu Virtual Machine](docs/ubuntu_setup.md)**
  
## Text Editor

You'll need a text editor designed for working with code. We recommend **[VSCode]**(https://code.visualstudio.com/), although you're free to use other tools of your own choosing.

To install Visual Studio Code on your Ubuntu VM:
* Go to Firefox and download Google Chrome (strongly recommended): install the .deb 64 bits for Debian/Ubuntu package
* Click Save file, rather than install with software center
* Click on the install driver and install, you will be prompted to provide the password you set up earlier.
* Then on Chrome, search for and download Visual Studio Code: .deb file for Debian,Ubuntu
* Click on the driver and follow through with the installation.

You can find newly installed apps under "Show Applications" in the side bar (at the bottom).
Right click on Visual Studio Code and Google Chrome and select "add to favorites" so they display on the sidebar.

On Mac, you can just download Virtual Studio Code as any other Application. 

## Shell Terminal

Mac and Linux both come with terminal programs, which provide a text-based interface to your operating system and related command-line tools. 

On Mac, use `Command + spacebar` to perform a Spotlight search for "Terminal". For a more pleasant shell experience, we strongly recommend installing [iTerm2](https://iterm2.com/).

On your Ubuntu Virtual Machine go to Applications (at the bottom of the sidebar) and search for "Terminal" - right click and add to *Favorites*

For the next steps, we recommend you find this page on Google Chrome and open it inside your Ubuntu VM, as there are lines of code you'll likely want to copy paste. 

## Version control

[Git](https://git-scm.com/) is a [version control](https://en.wikipedia.org/wiki/Version_control) system we use to save and submit code and data for projects.

[version control]: https://en.wikipedia.org/wiki/Version_control

### Linux

Open a terminal shell and run: 

```
sudo apt install git-all
```
### Mac

Install [Homebrew](https://brew.sh/), a software package manager used on the command line. Then use Homebrew to install git.

Open a Terminal shell (see [above](#shell-terminal)) and run the below commands. Along the way, you'll be prompted to agree to Apple licensing terms and to provide your laptop password.

```
xcode-select --install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
brew update
brew install git
```

> The commands above are based on Steps 1-3 of [How to Install Xcode, Homebrew, Git etc.](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#laptop-script) See the blog post for more details.

## Python

**Python 3.5 - 3.8**

Before installing Python, first open a Terminal shell and run: `python --version` or `python3 --version`

If you have a version between Python 3.5 and 3.8, you're all set.

If you have an older Python version (e.g. 2.7), follow the below instructions.

### Linux

Use [pyenv](https://github.com/pyenv/pyenv), a tool that allows you to install and manage multiple versions of Python. Run these commands from a shell:

```
# Clone pyenv
git clone https://github.com/pyenv/pyenv.git ~/.pyenv

# Add pyenv vars to bash config
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc

# Reinitialize shell
exec "$SHELL"

# Install build dependencies
sudo apt-get update
sudo apt-get install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

# Install python version 3.7.6
pyenv install 3.7.6
pyenv global 3.7.6
```

### Mac

Follow [these steps](https://docs.python-guide.org/starting/install3/osx/#install3-osx) but skip the installation of Homebrew, which should have been installed earlier when we set up [git](#version-control) (see above).


## Configure

Open a Terminal/shell. 

Download and run our configuration script. You'll need to answer a few questions along the way.

```
cd ~
#if you are on Linux install the following libraries
sudo apt install curl
sudo apt install geomview
sudo apt install python3-pip

#now run the configuration script
curl -O https://raw.githubusercontent.com/climatepolicydata/home/main/setup/configure_system.py
python3 configure_system.py
```

The configuration script will prompt you to peform a few additional steps:

1. [Upload your ssh public key to GitHub](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
```
#to generate a new ssh public key
 ssh-keygen -t ed25519 -C "your_github_email@example.com"
#This creates a new SSH key, using the provided email as a label

#When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.
#Also press Enter when prompted to provide a secure passphrase.

#Next, you need to add your key to the ssh agent
#Ensure the ssh-agent is running
eval "$(ssh-agent -s)"
> Agent pid

#add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
ssh-add ~/.ssh/id_ed25519

#add your public key to your Github account: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
#open your public key to copy
code ~/.ssh/id_ed25519.pub

```

3. [Create a GitHub API token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)
    Give your token a name, set to No expiration, and define the scope as 'repo'.

4. Open `code ~/.datakit/plugins/datakit-github/config.json` and replace `GITHUB_API_TOKEN` with the actual token from GitHub. Save the file.
    ![image](https://user-images.githubusercontent.com/96526387/147269590-bda9a198-dace-4b5c-a5c8-b2725c96ddd1.png)
    
    
> Congrats! If you are working from a Mac you're almost done. Skip to the [DataKit install](#datakit).


### Required libraries on Linux

* **Nodejs and Npm**
   A Nodejs version 10.19.0 is available from the Ubunty 20.04 repository, but for our purposes you will need a version > 12.0.0. We will install Nodejs using nvm.
   A shell script is available for the installation of nvm on the Ubuntu 20.04 Linux system.
   ```
   curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
   ```
   The nvm installer script creates environment entry to login script of the current user. You can either logout and login again to load the environment or execute the below command to do the same.
   ```
   source ~/.profile
   ```
   You can install multiple node.js versions using nvm. 
   Install the latest version of node.js. Here node is the alias for the latest version.
   ```
   nvm install node
   ```
   To install a specific version of node:
   ```
   nvm install 12.18.3
   ```
   Once you are done verify the installation by running:
   ```
   nodejs --version
   ```
   Make sure npm was installed by running:
   ```
   npm --version
   ```
   If not installed you can run the following:
   ```
   sudo apt install npm
   ```
* **Pyqt5**
  ```
  sudo apt-get install python3-pyqt5
  ```
* **Jupyter**
  ```
  pip3 install jupyter
  ```

### Editing your bash_profile or profile file
At this point you may have gotten a warning similar to this one:
```
The script is installed in '' which is not on PATH.
Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```
This will cause problems later on, to fix this follow these steps:
1. On Linux
* Open your ~/.profile file
```
code ~/.profile
```
* Ensure that the following code reflects the right path the warning pointed to
```
if [-d "$HOME/.bin"]; then
  PATH="$HOME/bin:$PATH"
fi
```
* This is setting PATH to include your private bin, where some packages are often installed. If you are getting the above warning you may need to adjust as follows. Rather than delete the previous code or edit directly, create a copy and comment out the old code, for backup. 
```
if [-d "$HOME/.local/.bin"]; then
  PATH="$HOME/.local/bin:$PATH"
fi
```
* Save the file and go back to the terminal
```
source ~/.profile
```
2. On Mac
The same error may occur when working from a Mac, in this case you'll want to add to your .bash_profile file the following code:
```
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi
```

## DataKit
> Before this step, make sure you've completed *all* [configuration](#configure) described above

[DataKit](https://datakit.ap.org/) is a command-line tool we'll use to manage code and data. It provides a standardized structure for projects and allows us to easily submit code to GitHub.

Run the following command to install DataKit:
```
pip3 install datakit-core datakit-project datakit-github pipenv PyGithub
#this will take a while

```
Follow [these instructions](docs/datakit.md) to complete the DataKit setup and create your first project.


