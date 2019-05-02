# git cheatsheet
This page gathers some instructions around the git functionalities we'll use throughout the workshop, so feel free to consult at any time!

## Clone

For full documentation on this command check the [git docs](https://www.git-scm.com/docs/git-clone).  

* To clone a repository follow the instructions on this [GitHub article](https://help.github.com/en/articles/cloning-a-repository)

## Create a branch

This [Git Branching doc](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) is a very comprehensive guide to Basic branching and merging, and it's worth the read if you're new to git and it's architecture.
Also, worth to know about [GitFlow](https://nvie.com/posts/a-successful-git-branching-model/), which is one of the most used branching models (either pure GitFlow or some variation of it).  

To create a new branch:  

1. `git checkout -b <your-branch-name>`

## Commit

For more info on commits, see [the docs](https://git-scm.com/docs/git-commit) and this useful article on [Saving changes](https://www.atlassian.com/git/tutorials/saving-changes) on git.  

To commit new changes:
1. Prepare the new files for the commit by adding them to the staging area:  
  * `git add <file-path>`  
  * If you have too many files to add (**and** are confident all files will need to be committed), you can opt for `git add --all`, which will add **all** the files into the staging area.  
  
2. Then, commit your code via `git commit`  
  * You'll be redirected to a text editor to add your commit message.  
  * If you're running it via Terminal within Visual Studio Code, you'll most likely have [Vim](https://www.vim.org/) as your editor.  
  Type `i` to start editing, and when you're ready, type `Esc`, then `:wq` to save and exit.  
  * Add a proper description to your commit message. Keep in mind that this message will be kept in the repository history, therefore it needs to be clear and descriptive as to what it's addressing/implementing. Ex: Workshop1 - Adding generated react app.  

## Push

For more info on pushing your changes, see this [GitHub article](https://help.github.com/en/articles/pushing-to-a-remote) and [the docs](https://git-scm.com/docs/git-push)
To push new changes:
1. With all the changes committed, the next step is to Push the code to GitHub:    
  * `git push origin <your-branch-name>`
  **Important**: The **first time** you Push your branch to a remote, you'll need to add the `-u` flag, which will tell git to create the branch remotely before pushing the code.


## Useful links

* [Writing good commit messages](https://github.com/erlang/otp/wiki/writing-good-commit-messages)  
* [GitHub Git cheatsheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet/)  
* [Learn git branching](https://learngitbranching.js.org/): Interactive resource for learning more about git and its concepts.  