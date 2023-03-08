---
title: "Basics of Git 1"
date: 2022-12-21
categories: [software]
image: images/thumbnails/Basics-of-git-1.png
url: /Basics-of-git-1/
draft: false
---

## Git in a nutshell
- *What is git?* **Ans:** Git is a program that constantly scans the file for changes and records them in order to create a version of those changes. That is why it is known as a version control system or version control tool.
- *Flow of github*
Ans:

![git-loop](/images/git_loop.png)

There are different github with different flags to do many task. But here we mainly focusing on the basic git commands. One of the basic command is status command to check on the repository.
- To see what have changed
		- `` git status``

We now will discuss about the various command for each stage of a project.

## Staging

A staging step in git allows you to continue making changes to the working directory, and when you decide you wanna interact with version control, it allows you to record changes in small commits.

- To add something to stage
		- ``git add --all``
		- ``git add --A``
- Reset the staged changes
		- `` git reset``
- add things to stage from current directory (not all)
		- ``git add .``
- add things but ignore or not stage the deleted one
		- `` git add * ``
- add specific file
		- `` git add one.txt``
		- `` git add myFolder/one.txt``
- add specific file types such as .txt or .js or .py
		 - ``git add *.js``
		 - `` git add *.txt ``

## Commiting the changes

- commit the changes in stage
		- `git commit`
		- `git commit -m "message for the commit"`
- From commit to unstage
		- `` git reset HEADS~``
*After this command changes have to be stagged then commit again*
- From commit to stage
		- `git reset --soft HEAD~1`


## Stashing the changes

- Lets  say you are working and you have to switch branch but you don't wanna commit. you can use stash command to stash away the chanages. Commands will be:
		- `git stash`
- Say we switched branches and done our work their and comeback. We want to see those stashed away lines we can use
		- `git stash pop`
- Similarly, you can use
		- `git stash apply`
This will apply whatever is stashed away, without removing it from the stash. This can be helpful if you wan to apply stashed changes to multiple branches.
- Multiple stash can be created and we can see the stash list command to see the stash list
		- `git stash list`
- To include untracked files in to the stash we use
		- `git stash -u`

## Reset & Removing
- If some file are deleted manually and it gets staged/commited and if we use
		- `git reset`
it will roleback the change in git but not in the directory itself.
Let's say that there are text files, one.txt and two.txt and we delete two.txt and stage/commit it. Then we use `git reset`  and show the status by `git status` we will see that delete have been reverted but file hasn't restored to working directory.
-To restore the file with git we have to use
		- `git reset --hard`
- We now will use git remove command to remove things from the repo.
		- `git rm two.txt`
		this will remove the file from the working directory and stage it simultaneously.
- If files are current with last commit and changes are made in some folder. If we remove it with `git rm file.name` it won't let us delete becase changes to file.name was not stagged or commited.
- If we still want to delete it without change being stagged and commited we have to use "force delete" flag. The command wil be
        - `git rm file.name -f`
- This command remove files from your local git repository. The --cached flag deletes the file from your git repository, it becomes an untracked file in your project folder. Note you have to commit the changes.
        - `git rm --cached file.name`
    In other words The Git rm –cached flag removes a file from the staging area. The files from the working directory will remain intact. This means that you’ll still have a copy of the file locally. The file will be removed from the index tracking your Git project.
    Let’s remove the settings.json working tree file from our repository but keep it in our project directory:
        - `git rm --cached settings.json`
    When we push our next commit, the settings.json file will be removed.
    As long as a file exists in your local working directory, you can add it back to your Git repository. You can do so using the git add command.

*My take*: Deletes the file from local and untracks it in the working directory.

- To delete a folder within a folder recursively, we use
 		`git rm -r foldername`

There are more basic commands. Which will be discussed in another article. If you are interested and want to learn more and want to go in depth of git check the [Git Documentation](https://git-scm.com/docs/git#_git_commands)
