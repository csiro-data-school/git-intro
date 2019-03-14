---
layout: episode
title: Basics
teaching: 20
exercises: 25
questions:
  - What is Git?
  - What is a repository?
  - How does Git operate?
  - How do I make commits?
  - How do I select what to commit?
objectives:
  - Learn to create Git repositories and make commits.
  - Get a grasp of the structure of a repository.
  - Learn how to inspect the project history.
  - Learn how to write useful commit log messages.
keypoints:
  - "Initializing a Git repository is simple: `git init`"
  - Commits should be used to tell a story.
  - Git uses the .git folder to store the snapshots.
---

## What is Git, and what is a Git repository?

- Git is a *version control system*: can record snapshots and track the content of a folder as it changes over time.
- Every time we **commit** a snapshot, Git records a snapshot of the **entire project**, saves it, and assigns it a version.
- These snapshots are kept inside a sub-folder called `.git`.
- If we remove `.git`, we remove the repository and history (but keep the working directory!).
- `.git` uses relative paths - you can move the whole thing somewhere else and it will still work
- Git doesn't do anything unless you ask it to (it does not record anything automatically).
- Multiple interfaces to Git exist (command line, graphical interfaces, web interfaces).

---

## Recording a snapshot with Git

- Git takes snapshots only if we request it.
- We will record changes always in two steps (we will later explain why this is a recommended practice):

```shell
$ git add somefile.txt
$ git commit

$ git add file.txt anotherfile.txt
$ git commit
```

- We first focus (`git add`, we "stage" the change), then shoot (`git commit`):

![Git staging]({{ site.baseurl }}/fig/git_stage_commit.svg
"git staging and committing"){:class="fig-responsive" style="max-width:70%"}

> ## Discussion
>
> What do you think will be the outcome if you stage a file and then edit it and stage it again, do this
> several times and at the end perform a commit? (think of focusing several scenes and pressing the shoot
> button only at the end)
{: .discussion}

---

## Configuring Git

**All the configuration we enter here will be stored in a file `~/.gitconfig`.**

When we use Git on a new computer for the first time,
we need to configure a few things. Below are a few examples
of configurations we will set as we get started with Git:

*   our name and email address,
*   what our preferred text editor is,
*   and that we want to use these settings globally (i.e. for every project).

Let's work through it together in Git Bash.

First, the following commands will set your user name and email address:

```shell
$ git config --global user.name "Your Name"
$ git config --global user.email yourname@example.com
```

The name and contact email will be recorded together with the code changes when we run `git commit`.

> ## Private email
>
> If you're using GitHub, and if you'd like to keep your personal email address private, 
> you can use a GitHub-provided no-reply email address as your commit email address. 
> [See here for further details](https://help.github.com/articles/about-commit-email-addresses/).
{: .callout}

> ## Line Endings
>
> As with other keys, when you hit <kbd>Return</kbd> on your keyboard,
> your computer encodes this input as a character.
> Different operating systems use different character(s) to represent the end of a line.
> (You may also hear these referred to as newlines or line breaks.)
> Because Git uses these characters to compare files,
> it may cause unexpected issues when editing a file on different machines. 
> Though it is beyond the scope of this lesson, you can read more about this issue 
> [on this GitHub page](https://help.github.com/articles/dealing-with-line-endings/).
{: .callout}
>
> You can change the way Git recognizes and encodes line endings
> using the `core.autocrlf` command to `git config`.
> The following settings are recommended:
>
> On macOS and Linux:
>
> ~~~
> $ git config --global core.autocrlf input
> ~~~
> {: .language-bash}
>
> And on Windows:
>
> ~~~
> $ git config --global core.autocrlf true
> ~~~
> {: .language-bash}
> 

## Setting a default text editor

When you work with Git, you often need to make small text files to describe a 'snapshot'. When this is necessary, Git will open whatever default text editor you have set. 
This means it's often useful to choose which text editor you prefer, and set it as the default. On your local machine, you can set it to be whatever you like, but if you're working on a remote system, you will only have access to editors that are available there.

Below is a list of commands to set the default editor to a list of common tools:

| Editor             | Configuration command                            |
|:-------------------|:-------------------------------------------------|
| Atom | `$ git config --global core.editor "atom --wait"`|
| nano               | `$ git config --global core.editor "nano -w"`    |
| BBEdit (Mac, with command line tools) | `$ git config --global core.editor "bbedit -w"`    |
| Sublime Text (Mac) | `$ git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl -n -w"` |
| Sublime Text (Win, 32-bit install) | `$ git config --global core.editor "'c:/program files (x86)/sublime text 3/sublime_text.exe' -w"` |
| Sublime Text (Win, 64-bit install) | `$ git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w"` |
| Notepad++ (Win, 32-bit install)    | `$ git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`|
| Notepad++ (Win, 64-bit install)    | `$ git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`|
| Kate (Linux)       | `$ git config --global core.editor "kate"`       |
| Gedit (Linux)      | `$ git config --global core.editor "gedit --wait --new-window"`   |
| Scratch (Linux)       | `$ git config --global core.editor "scratch-text-editor"`  |
| Emacs              | `$ git config --global core.editor "emacs"`   |
| Vim                | `$ git config --global core.editor "vim"`   |


> ## Git Help and Manual
>
> Always remember that if you forget a `git` command, you can access the list of commands by using `-h` and access the Git manual by using `--help` :
>
> ~~~
> $ git config -h
> $ git config --help
> ~~~
> {: .language-bash}
{: .callout}



