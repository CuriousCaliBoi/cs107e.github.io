---
released: true
permalink: /assignments/assign0/
title: "Assignment 0: Git oriented"
attribution: Assignment written by Maria Paula Hernandez, CS107e TA

toc: true
---

{% comment %}
Task list to copy/paste when creating PR for this assign:

**Before releasing assign0:**

- [ ] Review writeup/starter files/process (TA)
- [ ] Followup on issues from previous quarter postmortem ()

**To prep for assign0:**

- [ ]

{% endcomment %}


{% include duedate.html n=0 %}

<small>This assignment is not for a grade, but it's critical that you complete it on-time and understand the steps in the workflow you will be using for all assignments. If you run into troubles, please reach out on Ed or come by office hours!</small>

## Goals

Your goal for this assignment is two-fold:

1. Walk through and understand the git workflow we use in this course
2. Practice with your tools and refresh on background concepts

This assignment will give you practice with the standard tasks of getting starter code, editing files, 
committing changes, and submitting your work.

Have our <a href="/guides/cs107e-git#assignment-workflow" target="gwg">Git Workflow Guide</a> open in another browser tab. You will be following along with the section "Assignment Workflow" of the guide.

## Steps

### 0. Choose your editor and configure for use with git

In Lab 0, we asked you to explore text editors like vim and emacs. You
will be making heavy use of your chosen editor, so now is a good time to invest in
becoming comfortable and efficient with it.  This can be in the form of 
watching tutorial videos, reading manuals, bringing questions to OH, sharing tips with
each other, and practicing on your own.

Some git commands automatically open a text editor on your behalf. If you have not set an editor
in your git config, it uses a default choice.  Which editor does git use as its default?
Is this your preferred editor? If it is not, you can configure git to use the editor you prefer with the following command:

```console
$ git config --global core.editor [NAME-OF-YOUR-PREFERRED-EDITOR]
```

### 1. Pull starter code

To get the starter files, follow the instructions "Pull assignment starter code" in the <a href="/guides/cs107e-git#pull-assignment-starter-code" target="gwg">Git Workflow Guide</a>.

Pulling the starter code adds a new subfolder named `assign0` to  your `mycode` repo.
This folder contain the starter files for the assignment.

### 2. Answer background questions

In the `assign0` subfolder, find the file named `background.txt` and open it in your editor.

Add answers to the following questions.  Make sure each your response is clearly labeled (i.e.
we know what question it corresponds to) and reasonably organized.

> **Tip** If you're stuck on any of the questions, take a look at the guides section
> of the course website, post on Ed, or start reading some articles online!
> {: .callout-info}

1. What is the result of performing a bitwise OR of the following two
   hexadecimal numbers (include the result in decimal): `0x0f OR 0xff`. Now left
   shift that number by 24; what is the result in hexadecimal? Assume numbers are 32-bit.

2. How many milliamperes of current will flow through a 1.5K resistor connected
   to 3V on one end and 0V (Ground) on the other end?

3. Find a file in the directory `/etc` on your computer; tell us the name of the
   file and the number of bytes contained in that file. How many files and
   directories are contained in the first level of directory `/etc`? Include
   the commands you used to answer these questions.

4. Explain difference between an absolute and relative path. 

5. What do  `~`, `.`, `..`, represent? What happens when you pass them as arguments to the `cd` command?

6. Change directory to your `mycode` repo and find the folder named `cs107e`. What is
   the absolute path to this folder? How can you quickly change to this directory using the
   `CS107E` environment variable you created during your environment setup? Poke around
   a little in the `cs107e` folder to familiarize yourself to what it contains (various tools,
   header files, samples, etc.) Try out the `pinout.py` command.

7. What editor do you plan on using? What is your plan on learning
   how to best use your editor? (i.e. for people using vim, you can run the `vimtutor` command from your terminal). . Tell us a bit about how you customized your
   editor! Confirm you have configured git to use your chosen editor.

8. Explain what it means to have something on `$PATH`. 

9. Check out tools like tmux, tabs/panes in vim / eMacs, different terminals that provide tabs/panes such as iterm for mac, etc. 
   We want you to come up with a setup that works for you, your setup should give you the ability to have
   multiple terminals open, i.e you should be able to write your code in one window and make/execute that code in another without ever closing your code window.
   We cannot stress enough how much time and pain this will save you. Learn the key binds for your setup so you can switch between your code and your terminal window quickly.
   As an answer for this let us know what your setup is and what the key binds are to switch between your windows/tabs/panes .

10. Unix has many many useful commands, below is a list of a few that we feel everyone should know.
    You can run `man [command]` in your terminal to see the manual page and learn more.
    For each command give us a short description of what it does (in your own words) and an example of how you would use it.
    If there are options for the command try a few out and tell us about any you think would be useful 
    (i.e `rm` has an option `-r` which makes `rm` recursive allowing you to delete a directory not just a file.
    Be careful with that one btw, theres no getting your directory back!). 
    Commands to know: `cd`, `pwd`, `ls`, `cat`, `mkdir`, `rmdir`, `touch`, `rm`, `echo`.

11. Start typing a valid command into your shell, before you complete the command pause and try hitting tab a few times. What happens? Try it with `cd` as well.   

12. Again start typing in a command, before finishing this time hit `ctrl-c` , what happens? 

13.  Try running `sleep 10`, then enter `ctrl-c` , what happens? 

14.  What does `ctrl-r` do in terminal and why is this useful? How about the up arrow ? 

15. In git speak, what is a "commit"? What is a "branch"?
   If you're unsure, refer to our [git guide](/guides/git).

16. If there are resources (tutorials, blogs, videos, books, etc.) that you are finding particularly helpful as you get oriented with the environment and tools, tell us about them here and please share with everyone on our Ed forum!

Save your edits to `background.txt` and exit your editor.

### 3. Commit your changes locally and push to remote

Follow the instructions in "Assignment commit" of the <a href="/guides/cs107e-git#assignment-commit" target="gwg">Git Workflow Guide</a> to `git commit` a local snapshot, followed by `git push` to sync those changes to your remote repo.

After you do this, both the local and repo repositories should be up to date. Browse the `dev` branch of your remote repo on GitHub to confirm it is in sync.

<a name="submit"></a>
### 4. Make submit tag
Apply the tag `assign0-submit` to indicate these files are the ones to grade. Follow the instructions in the section "Assignment Tags"
in <a href="/guides/cs107e-git#assignment-tags" target="gwg">Git Workflow Guide</a> to create and push a tag.

Browse your remote repo on GitHub and confirm that your new tag is listed.

### 5. Open pull request

To indicate that your submission is ready for grading, you must have an open pull request.
Follow the instructions in the section "Assignment Pull Request" in the <a href="/guides/cs107e-git#assignment-pull-request" target="gwg">Git Workflow Guide</a>.

Confirm your submission using the "Assignment checklist" section of the <a href="/guides/cs107e-git#assignment-checklist" target="gwg">Git Workflow Guide</a> Congrats! (but wait, there is more, see below...)

### 6. Add photo file and edit README with your info

What's missing? A cherished course tradition is creating a Wall of Fame in Gates B02
to introduce all members of our community to one another. We
want to include you on our wall!

Find a photo of yourself that you would like to share. Copy this photo file into your `assign0` folder.

Edit the `README.md` file in the `assign0` folder to include the following information:
1. Your preferred name and pronouns 
2. Your hometown 
3. Your year and major

Add both the photo file and README.md to the staging index. Commit and push to your remote repo.

### 7. Move submit tag

To indicate this updated commit should replace your previous submission, move the submit tag.  Read the section "Assignment Tags" in the <a href="/guides/cs107e-git#assignment-tags" target="gwg">Git Workflow Guide</a> for instructions on how to move a tag.

Browse your remote repo on GitHub and confirm that your submit tag is placed on the commit which contains the correct content for all three files (`background.txt`, `README.md`, and your photo file).

## Success!
You have now successfully navigated the full assignment workflow:
- pull starter files
- edit files
- add and commit changes
- push to remote
- make submit tag
- open pull request
- update submission and move tag
- confirm results on remote repo on Github

And you're ready for the further adventures to come.
