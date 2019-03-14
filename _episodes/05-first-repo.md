---
layout: episode
title: Our first repo 
teaching: 30
exercises: 30
questions:
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

## Tracking a guacamole recipe with Git

We will learn how to initialize a Git repository, how to track changes, and how
to make delicious guacamole!

This example is inspired by [Byron Smith](http://blog.byronjsmith.com), for original reference, see
[this thread](http://lists.software-carpentry.org/pipermail/discuss/2016-May/004529.html).
The motivation for taking a cooking recipe instead of a program is that everybody can relate to cooking
but not everybody may be able to relate to a program written in e.g. Python or another language.

Let's start.

Make a new directory for this lesson. We'll store the Git repositories we make inside this directory.

One of the basic principles of Git is that it is **easy to create repositories**:

From inside your new directory:

```shell
$ mkdir recipe
$ cd recipe
$ git init
```

That's it! We have now created an empty Git repository.

If we use `ls` to show the directory’s contents, it appears that nothing has changed:

```
$ ls
```

But if we add the `-a` flag to show everything, we can see that Git has created a hidden directory
within `recipe` called `.git`:  

```
$ ls -a 
. ..  .git 
```

Git uses this special sub-directory to store all the information about the project, including all files and sub-directories located within the project’s directory. If we ever delete the .git sub-directory, we will lose the project’s history.

We will use `git status` a lot to check out to see what is going on with the repository:

```shell
$ git status

On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

We will make sense of this information during this lesson.


## So what exactly is a Git repository?

- Remember Git is a *version control system*: it records snapshots and tracks the content of a folder as it changes over time.
- Every time we **commit** a snapshot, Git records a snapshot of the **entire project**, saves it, and assigns it a version.
- These snapshots are kept inside the `.git` sub-folder.
- If we remove `.git`, we remove the repository and history (but keep the working directory!).
- `.git` uses relative paths - you can move the whole thing somewhere else and it will still work
- Git doesn't do anything unless you ask it to (it does not record anything automatically).

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

So that's the concept - let's do it for real.

Let's **create two files**.

One file is called `instructions.txt` and contains:

```
* chop avocados
* chop onion
* squeeze lime
* add salt
* and mix well
```

The second file is called `ingredients.txt` and contains:

```
* 2 avocados
* 1 lime
* 2 tsp salt
```

As mentioned above, in Git you can always check the status of files in your repository using
`git status`. It is always a safe command to run and in general a good idea to
do when you are trying to figure out what to do next:

```shell
$ git status

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	ingredients.txt
	instructions.txt

nothing added to commit but untracked files present (use "git add" to track)
```

The two files are untracked in the repository (directory). Going back to the photography analogy, you want to **`add` the files** (focus the camera)
to the list of files tracked by Git. Git does not track
any files automatically and you need make a conscious decision to add a file. Let's do what
Git hints at and add the files:


```shell
$ git add ingredients.txt
$ git add instructions.txt
$ git status

On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   ingredients.txt
	new file:   instructions.txt
```

Now this change is *staged* and ready to be committed (the camera is focused and we're ready to take the snapshot).

Let's now commit the change to the repository:

```shell
$ git commit -m "adding ingredients and instructions"

[master (root-commit) aa243ea] adding ingredients and instructions
 2 files changed, 8 insertions(+)
 create mode 100644 ingredients.txt
 create mode 100644 instructions.txt
```

Right after we query the status to get this useful command into our muscle memory:

```shell
$ git status
```

Now try `git log`:

```shell
$ git log

commit 787611f02dd6fc862c87359b804859caa5d2fdbd
Author: Alex Whan <alexwhan@gmail.com>
Date:   Wed Mar 13 17:07:44 2019 +1100

    adding ingredients and instructions
```

- We can browse the development and access each state that we have committed.
- The long hashes uniquely label a state of the code.
- They are not just integers counting 1, 2, 3, 4, ... (why?).
- We will use them when comparing versions and when going back in time.
- `git log --oneline` only shows the first 7 characters of the commit hash and is good to get an overview.
- If the first characters of the hash are unique it is not necessary to type the entire hash.
- `git log --stat` is nice to show which files have been modified.

---

> ## Challenge 1
>
> Add 1/2 onion to `ingredients.txt` and also the instruction
> to "enjoy!" to `instructions.txt`. Do not stage the changes yet.
>
> When you are done editing the files, run `git diff`:
> 
> ```shell
> $ git diff
> ```
>
> What does the output tell you?
>
> > ## Solution to Challenge 1
> >
> > ```
> > diff --git a/ingredients.txt b/ingredients.txt
> > index 2607525..ec0abc6 100644
> > --- a/ingredients.txt
> > +++ b/ingredients.txt
> > @@ -1,3 +1,4 @@
> >  * 2 avocados
> >  * 1 lime
> >  * 2 tsp salt
> > +* 1/2 onion
> > diff --git a/instructions.txt b/instructions.txt
> > index 6a8b2af..f7dd63a 100644
> > --- a/instructions.txt
> > +++ b/instructions.txt
> > @@ -3,3 +3,4 @@
> >  * squeeze lime
> >  * add salt
> >  * and mix well
> > +* enjoy!
> > ```
> > 
> > - The output shows which files are being compared - the "before" and "after" versions of the same file.
> > - The new lines added are prefixed with a `+` sign to show that they are new.
> {: .solution}
{: .challenge}

> ## Challenge 2
> 
> Stage and commit each change separately. For the second commit, don't use the `-m` flag.
> 
> What are the steps to run?
> 
> What happens if you don't use `-m`?
> 
> > ## Solution to Challenge 2
> > 
> > A possible example:
> > 
> > ```shell
> > $ git add ingredients.txt
> > $ git commit -m "add half an onion"
> > $ git add instructions.txt
> > $ git commit                   
> > ```
> > 
> > When you leave out the `-m` flag, Git should open an editor where you can edit
> > your commit message. This message will be associated and stored with the
> > changes you made. This message is your chance to explain what you've done and
> > convince others (and your future self) that the changes you made were
> > justified.  
> > 
> > Using a text editor (instead of `-m`) can be useful because you can include much longer commit messages.
> {: .solution}
{: .challenge}


### Writing useful commit messages

Using `git log --oneline` we understand that the first line of the commit message is very important.

Good example:

```
increase threshold alpha to 2.0

the motivation for this change is
to enable ...
...
```

Convention: **one line summarizing the commit, then one empty line,
then paragraph(s) with more details in free form, if necessary**.

- Bad commit messages: "fix", "oops", "save work", "foobar", "toto", "qppjdfjd", "".
- For your amusement: [http://whatthecommit.com](http://whatthecommit.com)
- Write commit messages in English that will be understood
  15 years from now by someone else than you.

---

## Ignoring files and paths with `.gitignore`

Some files should not be tracked in a Git repository. This includes files that are:
- specific to a particular computer
- contain sensitive information
- large, binary files
- compiled files

> ## Discussion
> 
> What could be the problems raised by committing the above files to a repo?
{: .discussion}


For this we use `.gitignore` files. Example:

```
# ignore R binary files 
*.RData
# ignore .exe files
*.exe
```

> ## Challenge 3
> 
> Make a new file called `my-personal-notes.txt`. Add some content to the file that describes your feelings about Git so far...
> 
> Since you might not want these comments seen by collaborators, make sure it is ignored by git
> 
> > ## Solution to Challenge 3
> > 
> > By adding the path `my-personal-notes.txt` to the `.gitignore` file, your personal thoughts about Git won't be added to any snapshots.
> {: .solution}
{: .challenge}

You can have `.gitignore` files in lower level directories and they affect the paths
relatively.

`.gitignore` should be part of the repository (why?).


### Keep your repo clean

- Use `git status` a lot.
- Use `.gitignore`.
- If you don't want to track a file, it should be listed in .gitignore.
- **All files should be either tracked or ignored**.

## GUI tools

We have seen how to make commits directly via the GitHub website, and also via command line. 
But it is also possible to work from within a Git graphical user interface (GUI):

- [Sublime Merge](https://www.sublimemerge.com/)
- [GitHub Desktop](https://desktop.github.com)
- [SourceTree](https://www.sourcetreeapp.com)
- [List of third-party GUIs](https://git-scm.com/downloads/guis)

---

## Summary

Now we know how to save snapshots (commits):

```shell
$ git add <file(s)>
$ git commit
```

And this is what we do as we program.

Every state is then saved and later we will learn how to go back to these "checkpoints"
and how to undo things.

```shell
$ git init    # initialize new repository
$ git add     # add files or stage file(s)
$ git commit  # commit staged file(s)
$ git status  # see what is going on
$ git log     # see history
$ git diff    # show unstaged/uncommitted modifications
$ git show    # show the change for a specific commit
$ git mv      # move tracked files
$ git rm      # remove tracked files
```

