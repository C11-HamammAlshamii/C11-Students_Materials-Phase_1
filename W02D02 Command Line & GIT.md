# Command Line & Git

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Command Line
- Github
- Git

## Command Line

### What Is The Command Line

The command line is a text interface for computers, they are used to run commands that perform some actions such as creating, editing, deleting files, running scripts, navigating through folders, etc...

Commands lines have different names like `consoles`, `terminals`, on Windows the default command line is called `command prompt` (cmd), and on macOS, it's called `terminal`.

The commands differ from one command line to another so we will install a new command line and it will be the default to use for all of the commands in the future, Click [Here](https://git-scm.com/downloads) to download a package to install git and git bash.

To run commands open git bash and type the commands to run then hit enter, here are some of the things that are possible to do using git bash.

#### Print Work Directory

use the following command to print the work directory (the current place where the terminal is)

```cmd
pwd
```

#### List

use the following command to list files and directories within the file system, and show detailed information about them.

```cmd
ls
```

#### Change Directory

use the following command followed by the path or name of the directory you wish to change the working directory to.

the path entered is usually relative to the current work directory.

```cmd
cd week4/lesson4
```

Use the following command to go back to the parent directory.

```cmd
cd ..
```

#### Creating files and folders

make directory is used to create a folder

```cmd
mkdir test
```

touch is used to create a file if not exist

```cmd
touch index.html
```

## Git & Github

### Github

GitHub is used for internet hosting for version control and software development, it has a lot of features that make it great to be used by developers, it creates versions of the software meaning it contains all the history for all the versions which makes it good in case there was a need to revert to an older version, it makes tracking changing across all the versions easy to do, it provides tools for teams to work together easily.

GitHub is an important platform to showcase the skills of an individual and an important part when looking for a candidate to hire since it shows examples of previous projects that the candidate has worked on.

Users can create public or private repositories on GitHub and these repositories are used to save code related to a certain project, if the repository is public then it can be viewed and accessed by anyone on the contrary to private repositories that need an invite to be accessed.

#### Creating A Repository (Repo)

1. Go to [Github](https://github.com/)
2. Login if not logged in
3. Click on the `Repositories` tab
4. Click on `New`
5. Fill the information
6. Create repository

### What is Git

Git is an open-source distributed version control system, it enables us to version our code, upload it to services like GitHub, share it easily with others, and more.

Git is mainly used through the command line, if you already have installed git from the previous section then it is ready to be used, to double check if you have git installed open git bash and run the following command `git --version`, if you see the version then it is installed correctly.

Here are some of the things possible to do using git

### Setup

Before working with git we need to connect the right email address and username, replace `email@domain.com` with your email, and replace `user name` with your GitHub username.

```cmd
git config --global user.email "email@domain.com"
git config --global user.name "user name"
```

#### Cloning

Cloning is the process used to get a copy of a repository locally on the user's machine.

Use the command `git clone` followed by the repository URL to clone it in the current work directory

```cmd
git clone https://github.com/User-Name/Repository-Name.git
```

#### Checking Changes

After closing a repo and making changes use the following command to check the changes files.

```cmd
git status
```

#### Staging Changes

After making changes the `add` command can be used to add the changes in the working directory to the staging area so it can be added to the next commit.

after the command add the name of the file that you want to add to the staging area.

```cmd
git add file-1
```

to add multiple file names that are separated by spaces to add multiple files at once.

```cmd
git add file-1 file-2 file-3
```

to add all the modified files to the staging area use the following command.

```cmd
git add .
```

#### Committing Changes

git commit creates a snapshot of the repository based on the new changes, when creating a commit you can create a commit message describing the changes that have been made, these messages need to be meaningful and concise.

to commit what is in the staging area use the following command.

```cmd
git commit -m "Describe the changes"
```

#### Pushing Changes

Pushing is the process of uploading the local repository commits to the remote repository found on platforms like GitHub.

to push the commits use the push command with the remote name, `origin` refers to the place where the repo was created and after that add the branch name, `main` is the default branch name, it used to be called `master`.

```cmd
git push origin main
```

#### Git workflow

- `git clone` the repo doesn't exist locally
- `git add` to add the changes to the starling area after modifying the code, use `git status` to check it before adding if needed
- `git commit -m "commit message"` to create a commit using the changes in the staging area
- `git push origin main` to upload your changes
- after making new changes repeat step 2 to 4
