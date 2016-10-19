Log
===

All of the below commands can be combined to give you even more contol of how you view the logs.

## Graph git log
Show the log in graph format adding on decorate to show ref names

```bash
git log --oneline --decorate --graph
```

Run the following to add an alias for this command

```bash
git config --global alias.lol "log --oneline --decorate --graph"
```

## Graph git log formatted
Show the git log formatted with custom formatting rules.

```bash
git log --oneline --decorate --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'
```

Run the following to add an alias for this command

```bash
git config --global alias.lolf "log --oneline --decorate --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'"
```

## Filtering logs
Filter by username

```bash
git log --author="Andy Mortimer"
```

## Filter by dates

```bash
git log --since="2 weeks ago"
git log --after="dd/mm/yyyy"
git log --after="dd/mm/yyyy" --before="dd/mm/yyyy"
```

## Greping the logs

```bash
git log --grep="Text to search for"
```

## Limiting the log output

```bash
git log -n 10
```

## Show difference between branches
The following will show all differences between whats in development and not in master.

```bash
git log master..development --oneline
```

## Searching for a text within a file  

```bash
git log -- filename -S blog
```
