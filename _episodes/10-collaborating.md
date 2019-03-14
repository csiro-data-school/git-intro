---
layout: episode
title: Collaborating through GitHub 
teaching: 25
exercises: 35
questions:
  - How can I access repositories already online?
  - How does version control scale from 1 to N users per repository?
objectives:
  - To practice cloning a new repository
  - To collaboratively edit a file and get the changes synchronised.
keypoints:
  - "`git clone` makes a local copy of a remote repository"
  - "Sharing a remote allows colleagues to collaboratively work on the same files"
  - Conflicts happen when two different versions of a file can't be automatically merged
  - Conflicts need to manually resolved and the changes committed
---

## Cloning a repository

Once a repository is on a public service like GitHub, other people can **clone** (make a local copy) of this repository and contribute changes. 

To practice this, we'll all clone the repository [https://github.com/csiro-data-school/ds3-git](https://github.com/csiro-data-school/ds3-git), make changes and push them back.

Visit the GitHub page for the repository, and click the `Clone or Download`. You can then use the `git clone` command to make a local copy.

Make sure you are not still inside your `recipe` repository before creating a new repository! Remember that repositories should not be nested inside each other.

```shell
$ git clone https://github.com/csiro-data-school/ds3-git.git
```

This creates a directory called "ds3-git" unless it already exists. You can also specify the target directory
on your computer:

```shell
$ git clone https://github.com/csiro-data-school/ds3-git.git some-name-that-i-chose
```

What just happened? **Think of cloning as downloading the `.git` part to your
computer**. After downloading the `.git` part, the latest state of the files is created locally.

> ## Challenge 1
> 
> Edit the `favourite-songs.txt` file in the newly cloned repository. Under your name, add a new line that contains the name of your favourite song.
> 
> Save the file with your change, and commit it locally.
> 
> Once you've made the local changes, push them back to the remote.
> 
> After your colleagues have pushed their changes, how will you get them back to your local machine?
{: .challenge}

## Conflicts

In the example above, each person created a new version of the file, and Git needed to work out how to merge those new versions. It was able to do that because the file already had names as placeholders, so it assumed those lines were unchanged. 

It is often the case when working collaboratively that two people will make changes that Git cannot automatically merge. In these situations, you need to manually tell Git which lines to keep and which to discard, or how the different lines should be arranged.

Let's imagine that I wanted to add my favourite song to the file, so I made a local change to the end of the file.

```
Alex
Achy Breaky Heart
```

However another colleague called Alex had also made a change to the end of the file (we'll make this change on GitHub to simulate a collaborator pushing a change)

```
Alex
Accidentally Kelly Street
```

The two repositories (local and remote) now have different histories. If we try to commit and push our local changes, Git can't know how to merge those differences. Instead it will give us an error:

```
$ git push
To github.com:csiro-data-school/ds3-git.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:csiro-data-school/ds3-git.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

In effect, Git is telling us it can't figure out how to merge those changes, so we need to do it manually. That means we need to get both versions into our local repository with a `git pull`:

```
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From github.com:csiro-data-school/ds3-git
   cc8a956..025818f  master     -> origin/master
Auto-merging favourite-songs.txt
CONFLICT (content): Merge conflict in favourite-songs.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Git tells us that there's a conflict in the `favourite-songs.txt` file, and that we need to resolve it, then commit the changes. If we open up the file, we can see that the two different versions are present. The local version is underneath the line starting with `<<<<<<< HEAD` and is separated from the remote version with `======`. The remote version then goes up until the line starting `>>>>>>>>>>`.

```
Alex
<<<<<<< HEAD
Achy Breaky Heart
=======
Accidentally Kelly Street
>>>>>>> 025818fcdf8a29d3cf80949e2643781ea961c2e4
```

To resolve the conflict, we need to choose which changes we want, and remove the extra lines. 

```
Alex 1
Achy Breaky Heart

Alex 2
Accidentally Kelly Street
```

> ## Visual merge tools
> Most GUI git clients offer visual merge tools to make resolving conflicts easier. These can be a great option, but won't be available in all environments, so being able to resolve a conflict at the command line is a very useful skill to have
{: .callout}

Now when we commit the changes and push them back, we can see that the local repo and the remote have identical histories.

> ## Challenge 2
>
> Open `conflict-file.txt` and answer the question.
>
> Save the file and commit your changes. 
>
> **Do not push until the instructor has modified the file on GitHub**
>
> Try pushing and read the error message.
>
> Pull the remote changes and resolve the conflict locally. Commit the changes.
{: .challenge}