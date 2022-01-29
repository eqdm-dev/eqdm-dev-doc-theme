---
title: Day 5
linktitle: Day 5
type: book
date: "2021-04-05T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---
## Taking a fork in the road

> In the Git glossary, you'll read this sentence: "In most cases, [main] contains the local development, though that is purely by convention and isn't required."  

🔑 Branches isolate your development from the rest of your work and from the master branch. Anytime you think, "I wish I had a copy of my repository," you should immediately think, "I'll just make a new branch!"  

Furthermore, branch names aren't prescribed by git. You are free to elect whatever works for you branching needs e.g. "BUG101"; "super-new-idea"; "hippo\branch\bot"  

## Commands in Play
* git branch [-d] [branch-name] 
* git branch [-v]
* git checkout [checkout-name]
	* [git checkout -b createbranch startingpoint](https://explainshell.com/explain?cmd=git+checkout+-b+createbranch+startpoint) -> Example: Using flags and options to create branch, starting from another branch, and switch to it in one step!
	* ‼️ This is also the command to restore a deleted branch by substituting DEL_BRANCH_SHA1ID for 'startingpoint'.
* git log --oneline
* git log --graph --decorate --pretty=oneline --all --abbrev-commit
	* git config —global alias.lol "log --graph --decorate
 --pretty=oneline --all --abbrev-commit" -> makes git lol alias to the long command!
* git branch [branch-name] [YOUR_SHA1ID] -> Example: Bugfix is 2 nodes behind master
* git check-ref-format
* git reflog -> Show all the times you changed branches
* git stash [list] [pop] -> Create a special commit for your WIP so that you may change branches with uncommitted changes

## 9.5.1 Using the GUI for branch work

{{< figure src="day5-02.png" caption="GITK pop-up for branch work." numbered="false" >}}
_Under macOS, use two fingers on the trackpad to access actions in GITK. Also, to get a better view of 'math' repo history, go to View on the GITK (Wish) app menu bar and click the 'Show local directory' radio button. Then hit 'F5 (Refresh)'._

Q: Deletion of branches off the tag 'four_files_galore': is it easier in the gitk GUI?
A: GITK GUI requires the two finger click on the tag name to access the proper action. On the CLI, its `branch -d my-unwanted-branch four_files_galore`.

## 9.5.2 Warm-up questions
1. If you create a branch in error, could you rename the branch instead of deleting it?  
A: You may: `git branch -m oops-branch rename-branch`  

2. In section 9.2.2, you had to search for the SHA1 ID of the commit containing the string 'Renaming c and d'. How would you identify this SHA1 ID when using the command `git rev-parse`?  

| Git Command                  | Returns                                  |
| ---------------------------- | ---------------------------------------- |
| `git rev-parse :/"Renaming"` | 6d813cb9145532f122d876834eefaed9cea0315b |
| `git rev-parse :/"c and"`    | 6d813cb9145532f122d876834eefaed9cea0315b |

3. Section 9.2.1 introduced a lengthy git log command. Look up what all the switches do! (Try running the command and leaving some of the switches out.)
A: This was `git log --graph --decorate --pretty=oneline --all --abbrev-commit` that was aliased in git-config to `git lol`.

4. What happens to the commits of a branch if you delete that branch?  
A: In Git, branches are just pointers (references) to commits in a directed acyclic graph (DAG) of commits. This means that deleting a branch removes only references to commits, which might make some commits in the DAG unreachable, thus invisible. But all commits that were on a deleted branch would still be in the repository, at least until unreachable commits get pruned (e.g. using git-gc). [version control - Does deleting a branch in git remove it from the history? - Stack Overflow](https://stackoverflow.com/a/2617160)

## Resources
[Git prompt completions](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh)
