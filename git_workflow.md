# **Git workflow**
[Git](https://git-scm.com/images/branching-illustration@2x.png)

## **Benifits**
Among the benefits of this workflow are the fact that **your work is completely isolated from everyone else's** and also **the reduction of error going to production.**
With this workflow, you prevent people from stepping on each others toes while working and ensure that the code that goes to production has been approved by a minimum number of developers.

## **Working on Branches**

*Branching means you diverge from the main line of development and continue to do work without messing with that main line.*

[Branch](https://cdn-images-1.medium.com/max/1000/1*XJmL7fWV4Coxt12AzHeG-A.png)

<font size=2> the main line is your master branch (main code). See how each branch is isolated from the main code until a certain point

##### create a new branch
    $ (master) git checkout -b my_new_branch
    > Switched to a new branch 'my_new_branch' 

##### push commits to repo 
    [...] some commits [...]
    $ (my_new_branch) git push origin my_new_branch

##### move back to master branch

    $ (my_new_branch) git checkout master
    > Switched to branch ‘master’
    $ (master) git checkout my_new_branch
    > Switched to branch ‘my_new_branch’

## **Code review**

*Instead of merging your branch back to master right away, a good practice of software development is to request your new code to be reviewed by other team members before.*

##### pull request
*Pull requests let you tell others about changes you’ve pushed to a repository on GitHub. Once a pull request is sent, interested parties can review the set of changes, discuss potential modifications, and even push follow-up commits if necessary.*

source: [GitHub help: Using pull requess] (https://help.github.com/articles/about-pull-requests/)

tip: review your own pull request before asking for reviews of your teammates


##### Refactoring/ Fixing Stuff

*Git allows us to change previously stablished commits: git interactive rebase*

    $ (some_branch) git rebase -i origin/master

If you already pushed your branch to remote, remember to use -f next time you push, since you've rewritten the your commit history:

    $ (some_branch) git push -f origin some_branch

<font color=#DC143C>**Warning** </font>
    **1. Pushing with -f is a very dangerous thing. Proceed with caution and always be sure that you're pushing to the right branch.
    2.NEVER rewrite the commit history of public branches (like master). This will truly mess your teammates work.**

## **Integrating your code**

Teams usually establish a minimum amount of reviews to get a pull request merged. Once you get the enough numbers of eyes on your code, designate someone to merge it! You can also merge yourself, but that's not the usual on most teams.
And that's it! Your code is now on your master branch, ready to ship to production.
