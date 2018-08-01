# git_squash
Best way I have found to squash all commits in a given branch

1. If you are on the branch which you would like to squash commits on, go ahead and commit or stash all changes (no need to push to origin).

2. Check out the master (or main) branch.

3. Run `git fetch origin`

4. Run 'git pull origin`

5. Checkout your branch on which you want to squash commits

6. Run 'git rebase -i master`

7. Pick / squash commits as you like, then save.

  7a. In VIM, to change multiple lines at the same time, enter visual mode with ctrl-v, then select all the 'pick's that you want to change and press 'x' to delete them.  Press ctrl-v again, and select all the lines you want to change, then type 'I' to enter text insertion mode, and type 's'.  Press escape.  's' will now be all the beginning of all those commits, telling git to squash those.

8. The editor will open again with all your commit messages.  Pick the commit message you would like or create a new one.  Delete the others.  Save.

9. Run `git push -f origin <branch_name>` (You have to force push because you are re-writing history)

10.  At this point you should see all your commits in your branch squashed into n commits.

One reason to squash commits is to clean up your history if you made lots of little commits.
Another reason is that if you work on a large team or a shared repo and don't make a practice of rebasing often, then when branches are merged into master the commits from multiple branches can overlap and make it difficult to roll-back changes for a particular merge request.

One commit is not necesary.  There should be one commit for each functional piece of work.


A second method involves a reset

# Switch to the master branch and make sure you are up to date.
git checkout master
git fetch # this may be necessary (depending on your git config) to receive updates on origin/master
git pull

# Merge the feature branch into the master branch.
git merge feature_branch

# Reset the master branch to origin's state.
git reset origin/master

# Git now considers all changes as unstaged changes.
# We can add these changes as one commit.
# Adding . will also add untracked files.
git add --all
git commit
