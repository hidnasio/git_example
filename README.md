# GIT

## what’s the purpose of a rebase

* To change the history of a branch. It's a destructive action.
* In general I use it for 2 things:
* * To get the latest changes from a remote branch (master, staging, production, etc)
* * To clean the history of my branch by squashing commits, changing commit messages, reordering commits, etc

## when is safe to do a rebase and when to do a merge

  Merges don't change the history of a branch so it's always safe to do a merge, but the history gets messy.

  * It's safe to do a rebase when you are the only person working on a branch and in the part of the history you are rewriting there aren't any merge commits.

## how to actually do it

  * To get the latest from a remote branch you can use
  ```
  git pull --rebase master
  or
  git fetch origin/master && git rebase origin/master
  ```

## To rewrite the history

  ```
  git log --oneline # find the first commit in the range you want to edit
  git rebase -i --root first_commit_in_range_hash
  # add the actions you want to do in the editor
  # resolve all conflicts and you are done
  ```

## how to recover if everything goes wrong (please don’t panic, reflog to the rescue)

Git tracks all the changes in references you do locally, this only works on the changes you do locally.

  ```
  git reflog
  ```
