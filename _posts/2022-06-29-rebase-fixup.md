---
layout: post
title: Rebase with fixup 🔧
---

Say goodbye to `squash` and _Hell Ye!_ to `fixup`

<!--more-->

Lets imagine you are rebasing a branch called `my-new-feature` onto `main`.
In order to do this you are doing an interactive rebase using the command `git rebase -i main` whilst you have the `my-new-feature` branch checked out.

(If you are using a GUI for git like the OP is using Git Extensions, if they are up to date they should also contain these new options)

Running `git rebase -i main` opens the following in your editor:

{% highlight ruby %}

pick 996b0 work in progress
pick 59f3a feature finished

# Rebase b6914..59f3a onto b6914 (2 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c <commit> to reword the commit message

{% endhighlight %}

Note the new `-C | -c` flag.

> s, squash <commit> = use commit, but meld into previous commit

> f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
                    commit's log message, unless -C is used, in which case
                    keep only this commit's message; -c is same as -C but
                    opens the editor 
---

Looking at our 2 commits:

{% highlight ruby %}
  
pick 996b0 work in progress
pick 59f3a feature finished
  
{% endhighlight %}
  
Let's imagine you want to meld them together (something which can be done with `squash` or `fixup`) but you want to only keep the helpful commit message of the second commit `feature finished`.

---

Using `fixup` as we have in the past like so: 

{% highlight ruby %}
  
pick 996b0 work in progress
f 59f3a feature finished
  
{% endhighlight %}

will not do what we want. It will meld the commits together but it will leave us with the `work in progress` commit message, which is not very helpful.

---

We could use `squash` like so: 

{% highlight ruby %}
  
pick 996b0 work in progress
s 59f3a feature finished
  
{% endhighlight %}

this will open a new editor which will allow you comment out the first commit message manually and persist the `feature finished` commit message. This does work but it forces you to have an extra manual step; *aint nobody got time for dat*

---

**This is where the new option we can pass to `fixup` is super handy.**

{% highlight ruby %}
  
pick 996b0 work in progress
f -C 59f3a feature finished
  
{% endhighlight %}

This will meld the commits together but discard the `work in progress` commit message and only keep the `feature finished` commit message.

---

These new options make `fixup` even more powerful and allows you to rely even less on using `squash` when you don't need to.
