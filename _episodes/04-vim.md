---
title: "Introducing Vim"
teaching: 15
exercises: 45
questions:
- "What is Vim?"
- "Why should I put in the effort to learn it?"
- "What are the alternatives?"
objectives:
- "Generate a new file using vim, add some content, save it, and exit vim"
- "Move around vim using the keypad"
- "Understand the use of, and change between, control, edit, and visual mode."
keypoints:
- "Vim is everywhere. If you know how to edit a file, save it and exit, you can work in any computing environment"
- "To enter `INSERT` mode, type `i`"
- "To get back to `NORMAL` mode hit `esc`"
- "To save a file, type `:w` in `NORMAL` mode"
- "To quit vim, type `:q` in `NORMAL` mode"
---

### Vim

Vim is a text editor. That is all it does. You cannot format a document, insert shapes, make a table with lines, use multiple fonts, highlight sentences, or print out with headings or margins.

Vim, however, is very good at editing text. Once you've mastered Vim, it is very powerful. You can find and replace chuncks of text using commands, copy and paste columns of data, and jump to a specified line number. 

Vim is also everywhere. If you are working on a computer with a shell (e.g. terminal or gitbash), then you have Vim, it's already there. And you can open it directly from the shell.

The problem is, however, that Vim is notoriously difficult to learn. 
 
Let's create a new file with Vim. First, open your shell, then type:

~~~
vim a_new_file.txt
~~~

Yay, a new file! Now, close that file. Type:

~~~
:q
~~~

Ta da! Congratulations, you've exited vim. 

> [one-million-developers-exit-vim](https://stackoverflow.blog/2017/05/23/stack-overflow-helping-one-million-developers-exit-vim/)
{: .callout}

### Adding content to a file in Vim.

So, you've created and exited a file with Vim. Your next challenge, is to put some text inside the file. Open your file again:

~~~
vim a_new_file.txt
~~~

Now, try and type some text. What's happening? You've seen this before in Juypter notebooks; you are currently in **normal**  (a.k.a. 'control') mode. To add text, you need to be in 'insert' or 'edit' mode.

To enter 'insert' mode, type `i`. You can now type! Add some text:

~~~
We interrupt this program to annoy you and make things generally irritating. I'm afraid I have no choice but to sell you all for scientific experiments.
~~~

> [random text generator for your general amusement](http://www.montypythonipsum.com/)
{: .callout}

How do you save your work? `ctrl-s` will not help you. First, you need to go back to normal mode by pressing `esc`, then type:

~~~
:w
~~~

(If you spend too much time working in Vim, your word documents start to accumulate random `:w` in them).

Now, you can safely quit vim again:

~~~
:q
~~~

Practice this. Re-open your vim document, enter insert mode, and add some more random text. 

There is also a command for saving and exiting all in one instruction. Press `esc`, then type:

~~~
:x
~~~

Phew!

You had little control over *where* your new text went in the last exercise. How do you move around in vim? In control mode, you can move one character at a time using the keys `k` (up), `l` (right), `h` (left), and `j` (down).

One you are in place, type `i` to enter insert mode on the left-hand-side of the current character. You can also type `a` to enter insert mode on the right-hand-side (i.e. 'a'fter) the character. Try this out, and add some more text.



There are lots of resources available to help you learn Vim. Vim even has its own tutorial. Exit vim, then from the shell, type:

> ## Vim's own tutorial:
> ~~~
> vimtutor
> ~~~
> work through the first 2 lessons
{: .challenge}

> ## Interactive Vim instructor:
> [open vim](https://www.openvim.com/tutorial.html)
{: .challenge}

> ## Let's get faster!
> [vim genius](http://www.vimgenius.com/)
{: .challenge}

> ## The Game
> [vim adventures](https://vim-adventures.com/)
> (you're a better gamer than me if you can work this one out).
{: .challenge}


