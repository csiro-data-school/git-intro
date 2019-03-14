---
layout: episode
title: Motivation
teaching: 10
exercises: 0
questions:
  - Why version control?
  - Why Git?
objectives:
  - Make sure nobody leaves the workshop without starting to use some form of version control.
  - Introduce git and its advantages
keypoints:
- "Version control is like an unlimited 'undo'."
- "Version control also allows many people to work in parallel."
---

## Why do we need version control?

[![Piled Higher and Deeper by Jorge Cham, http://www.phdcomics.com/comics/archive_print.php?comicid=1531](../fig/phd101212s.png)](http://www.phdcomics.com)

> ## Have you ever said or heard...
>
> - *"I will just finish my work and then you can start with your changes."*.
> - *"Can you please send me the latest version?"*.
> - *"Where is the latest version?"*.
> - *"Which version are you using?"*.
> - *"Which version have the authors used in the paper I am trying to reproduce?"*.
>
> **Then version control is for you**
{: .callout}


## What is version control?

There are lots of different tools that implement version control (generally referred to as **V**ersion **C**ontrol **S**ystems, **VCS**). They all have common features, including:

- A system which **records snapshots** of a project
- Implementation of **branching**:
  - you can work on several feature branches and switch between them
  - different people can work on the same code/project in parallel without interfering
  - you can experiment with an idea and discard it if it turns out to be a bad idea
- Implementation of **merging**:
  - tool to merge different versions of a file 

---

## Code becomes a disaster without version control


### Roll-back functionality

- Mistakes happen - without recorded snapshots you cannot easily undo mistakes and go back to a working version.


### Branching

- Often you want to experiment with an idea, or work on different approaches in one file - without branching this can be messy and confusing.
- You can simulate branching by copying the entire code to multiple places but also this will be messy and confusing.
- (We won't cover branching today, but in a future lesson)


### Reproducibility

- How do you indicate which version of your code you have used in your paper?
- When you find a bug, how do you know when precisely this bug was introduced
  (are published results affected? do you need to inform collaborators or users of your code?).


### What is the problem with this kind of "version control"?

Discuss the following directory listing:

```shell
mylib-1.2.4_18.3.07.tgz         somecode_CP_10.8.07.tgz
mylib-1.2.4_27.7.07.tgz         somecode_CP_17.5.07.tgz
mylib-1.2.4_29.4.08.tgz         somecode_CP_23.8.07_final.tgz
mylib-1.2.4_6.10.07.tgz         somecode_CP_24.5.07.tgz
mylib-1.2.5_23.4.08.tgz         somecode_CP_25.5.07.tgz
mylib-1.2.5_25.5.07.tgz         somecode_CP_29.5.07.tgz
mylib-1.2.5_6.6.07.tgz          somecode_CP_30.5.07.tgz
mylib-1.2.5_bexc.tgz            somecode_CP_6.10.07.tgz
mylib-1.2.5_d0.tgz              somecode_CP_6.6.07.tgz
mylib-1.3.0_4.4.08.tgz          somecode_CP_8.6.07.tgz
mylib-1.3.1_4.4.08.tgz          somecode_KT.tgz
mylib-1.3.2_22.4.08.tgz         somecode_PI1_2007.tgz
mylib-1.3.2_4.4.08.tgz          somecode_PI_2007.tgz
mylib-1.3.2_5.4.08.tgz          somecode_PI2_2007.tgz
mylib-1.3.3_1.5.08.tgz          somecode_PI_CP_18.3.07.tgz
mylib-1.3.3_20.5.08.tgz         somecode_11.5.08.tgz
mylib-1.3.3_tstrm_27.6.08.tgz   somecode_15.4.08.tgz
mylib-1.3.3_wk_10.8.08.tgz      somecode_17.6.09_unfinished.tgz
mylib-1.3.3_wk_11.8.08.tgz      somecode_19.7.09.tgz
mylib-1.3.3_wk_13.8.08.tgz      somecode-20.7.09.tgz
...
```

---

## We will use [Git](https://git-scm.com) to record snapshots of our work - why Git?

- Easy to set up - use even by yourself with no server needed.
- Very popular: chances are high you will need to contribute to somebody else's code which is tracked with Git.
- Distributed: good backup, no single point of failure, you can track and clean-up changes offline, simplifies collaboration model for open-source projects.
- Important platforms such as [GitHub](https://github.com), [GitLab](https://gitlab.com), and [Bitbucket](https://bitbucket.org)
  build on top of Git.
- Sharing software and data is getting popular and required in research context
  and [GitHub](https://github.com) is a popular platform for sharing software.
- However, *"Git is a four-handle, dual boiler espresso machine, not instant coffee."* [citation needed].
  Git isn't the most user friendly and has its design quirks but deep design
  is great and is definitely the most popular and what you are most likely to
  need to know. So we teach it.

