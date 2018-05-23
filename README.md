# git_squash
Best way I have found to squash all commits in a given branch

1. If you are on the branch which you would like to squash commits on, go ahead and commit or stash all changes (no need to push to origin).

2. Check out the master (or main) branch.

3. Run `git fetch origin`

4. Run 'git pull origin`

5. Checkout your branch on which you want to squash commits

6. Run 'git rebase -i master`

7. Pick / squash commits as you like, then save.

8. The editor will open again with all your commit messages.  Pick the commit message you would like or create a new one.  Delete the others.  Save.

9. Run `git push -f origin <branch_name>` (You have to force push because you are re-writing history)

10.  At this point you should see all your commits in your branch squashed into n commits.

One reason to squash commits is to clean up your history if you made lots of little commits.
Another reason is that if you work on a large team or a shared repo and don't make a practice of rebasing often, then when branches are merged into master the commits from multiple branches can overlap and make it difficult to roll-back changes for a particular merge request.

One commit is not necesary.  There should be one commit for each functional piece of work.
