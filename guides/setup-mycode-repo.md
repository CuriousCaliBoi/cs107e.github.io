---
title: "Guide: Initial git setup and mycode repo"
toc: true
quarterprefix: fall24
attribution: Written by Maria Paula Hernandez and Liana Keesing, incorporating work of past TAs
---

In CS107e, we distribute course materials as git repos and you will use git to access, manage, and submit your work. These repositories are hosted on GitHub. This guides walks you through the steps to do the initial setup of the `mycode` repo. The `mycode` repo is where you will manage all of your cs107e code.

> **Note** You should only need to follow the steps in guide once at the beginning of the course (unless you have to redo your setup for some reason). As always, be sure to ask for help if you run into any snags!
{: .callout-warning}

### Introduction
Each student has their own `mycode` repo, which manages all of the code for the coures assignments and labs.

We create a personal repository for each student on GitHub. This repo will be named `https://github.com/cs107e/{{page.quarterprefix}}-[YOUR-GITHUB-USERNAME]`, where [YOUR-GITHUB-USERNAME] is replaced with your actual github username.

Your personal repository that resides on GitHub 
is your __remote__ `mycode` repo. After we have set up your remote repo, you will connect it to a __local__ `mycode` repo on your  on your laptop. You will work on your code in the local repo and use git commands to exchange code between the local and remote repos.

Follow the steps below to set up your `mycode` repo.


### Step 1: Accept GitHub invitations

You should have received two email invitations from GitHub: an invitation for read-only access to the code mirror repo <https://github.com/cs107e/code-mirror.git> and another invitation for read-write access to your personal repo `{{page.quarterprefix}}-[YOUR-GITHUB-USERNAME]`. Once you receive and accept both invitations, you're ready to proceed.

### Step 2: Create SSH key and add to GitHub account

To streamline interacting with GitHub, you'll need to add an SSH
    key on your GitHub account. An SSH key authenticates your identity.
    To create an SSH key, enter the following
    command in your shell:

```console
$ ssh-keygen -t rsa -b 4096 -C "<your_email>"
```

After you press enter, you'll be prompted to choose a filename in which to save your
key. Accept the default by pressing enter. Next, you'll be prompted to enter a
passphrase for a key. If you want no passphrase, press enter. Otherwise, enter
your passphrase. If you choose to add a passphrase, you must enter that passphrase each time you push to or pull from GitHub .

{% include checkstep.html content="confirm the key was created" %}
Confirm the key has been created by looking for the key files in your `.ssh` directory:

```console
$ ls ~/.ssh/
```

You should see two files: `id_rsa` and `id_rsa.pub`. SSH uses public-key
cryptography, which requires a private key and a public key. `id_rsa` is your
private key and should never be shared. `id_rsa.pub` is your public key and can be shared to validate your identity.

Follow [these instructions from Github](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) to add your SSH key to your GitHub account.


### Step 3: Configure git identity
Use the commands below to configure your git identity so that your git actions are properly recorded. Be sure to replace `Pat Hanrahan` and `pmh@stanford.edu` with your own name and address. The last command just specifies that you want your repositories to merge on a git pull by default.

```console
$ git config --global user.name "Pat Hanrahan"
$ git config --global user.email pmh@stanford.edu
$ git config --global pull.rebase false
```

{% include checkstep.html content="confirm your git identity" %}
```console
$ git config --get-regexp user
user.name Pat Hanrahan
user.email pmh@stanford.edu
```

### Step 4: Create `cs107e_home` directory

Make a new directory named `cs107e_home` to store course material within your home directory. The tilde character `~` is shorthand for the user's home directory.

```console
$ mkdir ~/cs107e_home
```

Note: If you're using WSL, now is a good time to open File Explorer on your `cs107e_home` directory and "Pin to Quick Access" to add it the sidebar for future use. See [accessing WSL files from Windows](../install/wsl-setup/#files).

### Step 5: Make local clone

> **Note** In the commands below, replace any reference to `[YOUR-GITHUB-USERNAME]` with your __actual GitHub username__.
{: .callout-warning}

In your browser, visit the page
`https://github.com/cs107e/{{page.quarterprefix}}-[YOUR-GITHUB-USERNAME]` to see the contents of your remote repo.
It should have only a single file: `README.md`, which lists the name of your
repo and nothing more.

Make a local clone of your repo.
   This is a copy of the remote repo that lives locally on your computer.
   You are doing to store your repo in the parent directory `cs107e_home` that you just made.
   Execute the following terminal commands to make your local `mycode` repo.

```console
$ cd ~/cs107e_home
$ git clone git@github.com:cs107e/{{page.quarterprefix}}-[YOUR-GITHUB-USERNAME].git mycode
```

Change to your repo and use `ls` confirm the files match those you see when browsing your remote repo on GitHub.

```console
$ cd mycode
$ ls
$ cat README.md
```
You'll notice that the command `cat` will just print the contents of a file to your terminal. This is a useful command that you'll use again!

### Step 6: Create `dev` branch (local and remote)

The `master` branch in your repo is "write-protected," which means
that you will not be able to directly modify this branch on GitHub. Instead, you'll do your work
on a separate `dev` branch. To create this
branch, change to your repo and execute the
following commands:

```console
$ cd ~/cs107e_home/mycode
$ git branch
$ git checkout -b dev
$ git branch
```

When you execute the first `git branch` command, notice how there is only a single
branch listed: `master` and there is an asterisk next to `master`. This asterisk
identifies which is the currently checked out branch. When you run the second
`git branch` command, you should have two branches (`master` and `dev`) and the
asterisk is now next to `dev`.

The new `dev` branch you created only exists in your local repo; next you will
connect it to a new remote branch of the same name. Use `git branch` to confirm that you are on the
`dev` branch and execute the following command:

```console
$ git push --set-upstream origin dev
```

If you return to your GitHub repo in your browser, you should now find a `dev` branch in the branches dropdown menu.

### Step 7: Add code-mirror remote

Now you will configure your local repo to have an additional remote connection to the code mirror repo. The `code-mirror` repo is where we place the starter code for labs and assignments. Execute the following commands to add the remote `code-mirror` repository for which you ealier accepted the invitation.

```console
$ git remote -v
$ git remote add code-mirror git@github.com:cs107e/code-mirror.git
$ git remote -v
```

When executing the first `git remote -v` command, you should have only a single
remote: `origin`. `origin` is a shorthand way of referring to your remote repo
on GitHub. The `git remote add` command adds a second remote. This second remote
is `code-mirror`, which is a shorthand way of referring to the code mirror
repo on GitHub. The second `git remote -v` should show you both remotes:
`origin` and `code-mirror` and the URLs that they represent.

Before we move on, we actually need to pull some code from the `code-mirror` remote repo. If you look at <https://github.com/cs107e/code-mirror> (which we call `code-mirror`), you'll see that it contains a folder called `cs107e`. That folder, if you look inside, contains a number of folders (like `bin`, `include`, and `src`) filled with files. Those files will serve as the base code for CS107e, and the code you write will sometimes reference those files (for example, all the `.h` files you'll reference in this class are located in the `include` folder). To update your local `mycode` repo to include the `cs107e` folder, use the following command:
```console
$ git pull code-mirror master
```
{% include checkstep.html content="confirm the cs107e folder is on your local machine" %}
```console
$ cd ~/cs107e_home/mycode
$ ls cs107e
bin  extras include  lib  other sample_build  src
```
You should now see a list of the folders inside the `cs107e` folder.
    
### Step 8: Edit shell configuration file
While we now have the `cs107e` folder (filled with all of its goodies) safely tucked away in our `mycode` folder, we need to tell our shell environment that it exists so that we can reference it easily when we make our code later. 

What does that mean? If we needed to, we could refer to the `cs107e` folder every time by its location: `~/cs107e_home/mycode/cs107e`. But that's so long---and if I made my path any different than yours, then suddenly all of my code would break. So instead, we can use a nickname for the `cs107e` folder, since we're going to need to refer to it frequently.

When opening a new shell, the environment is initialized by reading a configuration file in your home directory. Editing the configuration file allows you to set the initial state of your shell to have this nickname. Here are the steps to do that:

1. Determine the name of the configuration file for your shell. The name depends on which shell you are using. Use the command `echo $SHELL` to see your shell. Your shell is likely `zsh`, although it might be `bash` if your account was created on an older macOS.
    ```console
    $ echo $SHELL
    /bin/zsh
    ```

    If your shell is `zsh`, the configuration file is named `.zshrc`.  If your shell is `bash`, the configuration file is named `.bashrc`.  For any other shell, please ask a CA for help.
2. Find out if you already have an existing configuration file or create it if needed. Change to your home directory and list the files. Filenames starting with a dot are hidden in a directory listing by default. Use the command `ls -a` to list all files, including hidden ones:
    ```console
    $ cd ~
    $ ls -a
    .    .bash_history   .bashrc     cs107e_home     .python_history 
    ..   .bash_logout    .config     .profile        .viminfo
    ```
(The filenames listed in your directory may be somewhat different, don't worry!) Look through list to see if there is already a configuration file for your shell. 
    If not listed, use `touch` to create an empty file with the appropriate name:
    ```console
    $ touch ~/.zshrc     # OR touch ~/.bashrc if your shell is bash fron step 1
    ```

3. Open the configuration file in a text editor and append the following two lines verbatim:
    ```
    export CS107E=~/cs107e_home/mycode/cs107e
    export PATH=$PATH:$CS107E/bin
    ```

    The first line sets the environment variable `CS107E` to the path to where the class files are stored. The second line adds our `bin` subdirectory to your executable path. 

4. Use the `source` command to read the updated configuration file into your current shell:
    ```console
    $ source ~/.zshrc    # OR source ~/.bashrc
    ```

{% include checkstep.html content="confirm current shell is properly configured" %}
```console
$ echo $CS107E
/Users/student/cs107e_home/mycode/cs107e
$ ls $CS107E/lib/libmango.a
/Users/student/cs107e_home/mycode/cs107e/lib/libmango.a
$ which pinout.py
/Users/student/cs107e_home/mycode/cs107e/bin/pinout.py
```

The configuration file is persistent and should be automatically read when creating a new shell in the future. 

{% include checkstep.html content="confirm shell configuration is persistent and future shells properly configured" %}
Close your current shell and open a new one. Repeat the check step above in the new shell and confirm the new shell is also properly configured.

If you confirm your configuration is persistent, skip the step below. If it is not persistent and you are using  `bash` and the macOS Terminal, use the additional customization below to add persistence.

{: start="5"}
5. (only if needed) Find the file named `.bash_profile` in your home directory. If no such file exists, use the `touch` command to create an empty file with that name. Open that file in a text editor and append the following line verbatim:
    ```
    source ~/.bashrc
    ```

Repeat the previous check step with a new shell to confirm your configuration is now persistent.

### Step 9: Celebrate! You've set up your code base! 🎉
Yay! That was a lot of steps you just did! Once you've finished this, the next step is to put in some work to understand just how to use this awesome setup you've created. To do that, check out the [CS107E Github workflow guide](/guides/cs107e-git).
