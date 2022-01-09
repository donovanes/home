# Automating workflow with DataKit

- [Overview](#overview)
- [Install](#install)
- [Preview](#preview)
- [First project](#first-project)
- [Daily use](#day-to-day-with-datakit)

## Overview

[DataKit][], an open-source command-line tool created by the Associated Press. DataKit was [designed in a team environment][] to bring sanity to data projects. Among other things, it helps standardize project structures, easily share code and data with teammates, and even publish data as part of story packages.

[DataKit]: https://datakit.ap.org/
[designed in a team environment]: https://www.rjionline.org/stories/ap-datakit-intro

It also makes it easy to customize workflows to suit different teams and individuals.

DataKit will help us streamline our workflow while applying best practices from the worlds of data science and software. Among other things, it will help us:

* Create standard project structures for all code work
* Use [virtual environments](https://docs.python.org/3/tutorial/venv.html) for Python (using [pipenv](https://docs.python-guide.org/dev/virtualenvs/))
* Save code and data in [version control](https://en.wikipedia.org/wiki/Version_control) ([git][])
* Publish our work to GitHub, making it easy to collaborate with other analysts and to open-source if we choose. 
* Easily share our work with colleagues

[git]: https://git-scm.com/book/en/v2

## Install

Follow the steps in [Tech Setup - DataKit](tech_setup.md#datakit). *Note, you must first work through the preceding steps in the Technical Setup.*
See the [Datakit documentation](https://datakit-github.readthedocs.io/en/latest/install.html) for more details.

## Preview

When you run DataKit on the command line, it will ask you a series of questions that help configure the new project. The questions will often have default values shown in square brackets `[]`. 

You can simply hit `return` to accept the defaults, or type in an answer as necessary. Below is an example session demonstrating the workflow.

Some important bits to note:
* A new project folder (i.e. a new git repository) has been created on your virtual machine (if you are on Mac, it will create it in your local machine). 
* If you look inside the new folder on your machine, you should see a bunch of initial project files and directories have been created.

## First Project

The first time you run DataKit will be a little bit different than subsequent uses. On this first run, we need to specify a template. 
When you first run DataKit, it will install this template locally, simplifying future usage.
Three [templates](https://github.com/cookiecutter/cookiecutter) are available to use, choose the one that will suit most of your projects:

To kick off the process, run the following. 
> Type "Test Project" when prompted for the `project_name`. For all other prompts, hit `return` to accept the default values.

```
#create a directory called 'projects'
cd ~
mkdir projects

#navigate to your projects directory
cd projects

#create your first datakit-project
##python
datakit project create -t https://github.com/associatedpress/cookiecutter-python-project.git

##r
datakit project create -t https://github.com/associatedpress/cookiecutter-r-project.git

##generic
datakit project create -t https://github.com/associatedpress/cookiecutter-generic-project.git
```
This process prints a lot of information to the shell.
You'll also see some reminders about next steps for working with the new project -- specifically, navigating into the newly created repository on your shell and installing some Python libraries.

```
# Navigate to the newly created project folder
cd test-project/
# Install Python dependencies
pipenv install
```

Next, you should activate the virtual environment:

> Note, this is mainly needed for Python work, but it's a good habit in general.
```
pipenv shell
```

At this point, you could add new files to the project, for example a Python or Bash script. Normally you'll use a text editor such as Visual Studio Code to create and save new files.

Just make sure to save code files somewhere *inside* this newly created project folder. 

## GitHub Integration
To integrate the project with GitHub, navigate into the newly created project directory and execute the following command:
```
cd test-project
datakit github integrate
```
The above should trigger a series of prompts that allow you to select the GitHub account where the new repo should be created, and whether to make the repo private or public.

The command will auto-generate the GitHub project, link your local code to the new project, and push the newly generated project skeleton to GitHub as your first commit.

### Working with git

You should think of this new project folder as much more than a mere collection of files and directories. Instead, it's more akin to a system for storing all of the incremental changes made to your files over time. 
This is an incredibly powerful and [useful way of working](https://www.git-tower.com/learn/git/ebook/en/command-line/basics/why-use-version-control/), but it does require a bit more overhead to manage.

To save and *push* code to GitHub follow these steps:

Make sure you've navigated *inside* the project directory:

```
# Navigate to the project folder
cd test-project/
# Activate the environment, if you haven't already
pipenv shell 

#Check which files have changes
git status

#Save files locally to git
git add filename

#Commit the files to GitHub and add a message/label, in this case "test commit"
git commit -m "test commit"
```
![image](https://user-images.githubusercontent.com/96526387/147275921-050dd15f-cfb4-4457-a951-62f2d706ef9d.png)

When you're done working, deactivate the virtual environment:

```
exit
```

Congratulations, your work should now be saved in a private repo on GitHub!!

## Day-to-day with DataKit

In the future, you can use DataKit to create new projects by simply running `datakit project create`, followed by the other commands mentioned above.

You should get into the habit of saving and publishing your work to GitHub whenever you add, change or delete files. This applies to both code and data files.

If you're making changes to a previously created project, you won't need all of the commands mentioned above. 

Here's the short list of commands you'll need when working with an existing project:

```
# Navigate to the project folder
cd test-project/
# Install Python dependencies (e.g. pandas, jupyterlab, altair...), typically
# after the project is first created
pipenv install
# Activate a sandboxed environment for this project
pipenv shell
# Save your work locally to git
git status
git add filename
# Push work to GitHub
git commit -m ""
# When you're done working,
# deactivate the virtual environment
exit
```



