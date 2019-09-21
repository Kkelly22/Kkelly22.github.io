---
layout: post
title:      "Read/Write Repository Permissions"
date:       2019-09-21 21:04:56 +0000
permalink:  read_write_repository_permissions
---


I was recently asked to make changes to someone else's repository and submit a pull request - a common practice among developers working together.  Like I always do, I went to the repository on GitHub, cloned the repo via SSH, and typed "git clone git@github.com:path/to/repo".  I was able to clone and pull successfully, and I even got as far as creating a new branch via "git checkout -b new-branch-name", however I was not able to push when I attempted to execute "git push origin new-branch-name".  I immediately got the error "remote: Repository not found.  fatal: repository 'https://github.com/path/to/repo/' not found".

To summarize my steps at a quick glance, this is what I was attempting to execute:

git clone git@github.com:path/to/repo
git pull origin master
*Already up to date*
git checkout -b new-branch-name
*Switched to a new branch new-branch-name*
git push origin new-branch-name
*remote: Repository not found.  
fatal: repository 'https://github.com/path/to/repo/' not found*

I started scouring Google for other people's experiences with this issue, and I found this problem basically boils down to three main things:

1) Check to make sure you spelled the repository correctly when executing your 'git clone' statement.  Since I copy and pasted mine directly from the GitHub repo, I felt confidently this was not the issue.

2) Check to make sure your SSH authentication is set up correctly.  I checked the SSH keys I had in place by typing "ls -al ~/.ssh" in my terminal, and confirmed a public and private SSH key existed (for example id_rsa.pub and id_rsa).  I've also been using this SSH key for other current GitHub connections, so I felt confidently this was also not the issue.

3) Check to make sure you have read/write access to the repository.  Interestingly enough, there were **two** hints that this was the cause of my problem, but I initially ignored them.  First, my forking capability was disabled, and secondly I could not create a branch by typing in a unique branch name.

After some time and additional research, I looped back to the email I received when I was first added to the list of contributors, and the email indicated I had received *read* access to the repository (note the missing *write*).

Moral of the story - always check your permissions!
