Diff
===

Use the following to get a breakdown of all the files that contained changes HEAD can be replace with a SHA to look at older commits

```bash
git diff --stat HEAD
```

This example will only show the stats for files containing the text **Blog**

```bash
git diff --stat HEAD -S Blog
```

## Shows diffs between local and remote branch

```bash
git diff origin/development development
```

or just stats

```bash
git diff --stat origin/development development
```
