# Technical Setup (Software, tools, etc.)

> See the [Technical FAQ page](tech_faq.md) if you run into snags and/or [report an issue](/issues).

- [Services and platforms](#services-and-platforms)
- [Windows](#windows)
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
