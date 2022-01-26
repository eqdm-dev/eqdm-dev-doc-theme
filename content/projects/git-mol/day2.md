---
title: Day 2
linktitle: Day 2
type: book
date: "2021-03-23T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---
## Doing init
Using a freshly `init` repo, we are going to do a bunch of small edits to watch how Git conveys information back to the local repo owner.

Create a new repo in a new empty directory -> `git init`
Create some artifact for git:

1. `touch README.md`
2. `git add README.md && git commit -m "Add empty document"`
3. `echo "no longer an empty document" > README.md`
4. `git commit -am "Second commit" # (szf) Add and commit message on one-line`

Here’s where I diverged from the lesson plan and treated my _README_ file like it was a bash script.

Making small edits and several commits, I was able to see the circumstances like:
 
![Diagram of a git flow](/git-mol/day2-02.png "The dev cycle: Working area, Staging area , Commit history")

From right to left, I have:

1. Created my README file, added, and committed it (in this case, I had previously marked the file executable, and added a variable to the file with echo of the same variables value)
2. I have made edits to same file and added it (then I enhanced the file-as-script and added, but not committed, the change)
3. I have made more edits to the file (finally, I removed the single variable echo as I have done more work on the file-as-script)

![Diagram of a git status](/git-mol/day2-03.png "`git diff` or `git diff —staged` can show the facet of the dev cycle")

## Commands of Note
```
git diff
git diff --staged
git add --dry-run .
git log
git log --stat
git log --shortstat --oneline
```

##  Expressing my Skillselves

{{< figure src="/media/git-mol-day2-01.png" caption="…/.git/rebase-merge/git-rebase-todo" numbered="false" >}}
_After doing multiple commits, it would seem that doing something unconventional like adding the execute bit to a text file and adding script code should support and inform the commit history._

☝️Using `git rebase -i HEAD~N`  (where N is positional number), I was able to tag the errant line with the `reword` command and change the message in an interactive session. Nice!

## Lab
Q. What is another way to call `git diff —staged`?  
A: `git diff —cached` and `git diff HEAD README.md` produce the same output

Q. What is the short form of `git add . —dry-run`?  
A: `git add . -n`

Q. How do you display line numbers to your file via the `cat` command?  
A: `cat -b`

Q. The `—oneline` switch that you passed to git log is shorthand for a longer git log command. What is it?  
A: `git log —pretty=oneline`  shows full SHA1 hash

Q. The `-a` switch to git commit (to automatically pass files to git add) has a longer alternative switch that is surprisingly not `—add`. What is it?  
A1: Could be `—all`?  
A2: You can interactively have git ask what you want to do with a code hunk via `git add . -p` for **patch** mode.