---
layout: episode
title: In-browser session
teaching: 20
exercises: 0
questions:
  - Where are we heading?
objectives:
  - See an existing repository in action.
  - Browse the history.
  - See the big picture first before we dive into details.
keypoints:
  - "GitHub is a service that uses git and provides functionality to collaborate with other people"
  - "We can browse the history of the contents of repositories and see who made which changes"
---

# In-browser session

- We will explore and visualize an **existing Git repository** on GitHub
- The goal of this episode is not to teach GitHub, but rather to get a glimpse of the 
wider picture before going into the details.

---

## Why

- Often our first contact with Git is an existing repository
- The existing repository is often on GitHub (but this demonstration applies
  equally well to GitLab or Bitbucket).
- It's good to see the social aspect to know what our end goal is.

---

## Don't Panic 

- If you are new to version control, don't worry about the details of the steps. Focus on what we can learn about the repository

---

## Demo

We'll start with a very simple 
[existing repository](projec://github.com/csiro-data-school/example-repo)
that contains a brief history from a few different people

- History
  - Explore the [repository](https://github.com/csiro-data-school/example-repo).
  - Explore the history.
  - Browse the commit.
  - Note that there are [branches](https://github.com/csiro-data-school/example-repo/network).
- Reproducibility
  - Demonstrate the ['blame' feature](https://github.com/csiro-data-school/example-repo/blame/master/scripts/cows-analysis.R).
- Collaboration
  - You can refer to [code portions](https://github.com/csiro-data-school/example-repo/blob/7f40e7626bc6e20dcf912f15913121d35c1ec294/scripts/cows-analysis.R#L8-L9)
    (so much simpler to send a link rather than describe which file to open and where to scroll to).
  - Demonstrate a [pull request](https://github.com/csiro-data-school/example-repo/pulls)
  - Browse the [network](https://github.com/csiro-data-school/example-repo/network).
  - See [contributors](https://github.com/csiro-data-school/example-repo/graphs/contributors).
- Releases
  - Explore the [history](https://github.com/csiro-data-school/example-repo/commits/master) again.
  - Create a [release](https://github.com/csiro-data-school/example-repo/releases).

While some of these are GitHub features, it all can be done on other sites, or
by yourself without GitHub at all.
