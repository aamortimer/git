Revert
===

## Revert commits/merge

```bash
git revert sha ## revert a commit
git revert sha -m 1 ## revert a merge
```

Generate a new commit that undoes all of the changes introduced in <commit>, then apply it to the current branch.

> Use the option -n or --no-commit flag to leave the reverted changes in your working directory and not automatically commit them. Useful if you need to edit files further to complete the revert or possibly revert more than one commit.

