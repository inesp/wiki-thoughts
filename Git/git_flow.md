# Add/Remove a file

```bash
git add <file/folder>
git add .
git add -A
```

## Patches

```bash
git add <file> --patch
```

## Remove from staged files

Staged files means files which have been added with `git add`.

```bash
git reset
git reset <file/folder>
```

## Lose all changes

Lose all changes on existing files:
```bash
git reset --hard  # cannot do hard reset with paths
git checkout <file/folder>
```

Delete new, unstaged files: **Do it with a GUI tool.** 
If you do it with git's clean command, you might delete the
wrong files and the delete files will trully be gone!
If you still wish to run git clean, first run with `-n` to 
test run the command, to see which  it will delete. 
(`-d` is for directories, `-f` is needed because git configuration
variable `clean.requireForce` is usually set to true)
```bash
git clean -nfd
git clean -fd
```

# Check status and changes

General state of the git repository:
```bash
git status
```

Changed lines in modified files:
```bash
git diff
git diff --staged
```

Other formats of changes (usually used as the input for other scripts):
```bash
git diff --stat
git diff --name-only
git diff --name-only | grep -E ".(py|js)"
```

Filter the `git diff`:
```bash
# ignore deleted files
git diff --name-only --diff-filter=d
# show only deleted files
git diff --name-only --diff-filter=D
```

To see the changes in existing commits:
```bash
git diff --stat <commit-hash-older> <commit-hash-newer>
git diff --stat <commit-hash-older>^ <commit-hash-newer>
```

## Git Log - History tree

The best way to see the history is with the alias `git lg`. Lg is the alias for a pretty log tree. 
Set it up with:
```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

Useful log commands:
```bash
git lg -5
git lg --since=2.weeks
git log --oneline
```

Look into the history of 1 file and follow it beyond its renamings and movements:
```bash
git log --follow -p <file>
```
The `-p` option creates a patch for every change. This makes it easy to see what the change was.

Show all commits adding or removing the string "func_name":
```bash
git log -S "func_name"
git log -S "func_name" -p
git log -S "func_name" --stat
git lg -S "func_name"
```
