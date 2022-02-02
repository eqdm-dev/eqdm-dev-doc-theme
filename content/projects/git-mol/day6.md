---
title: Day 6
linktitle: Day 6
type: book
date: "2021-04-06T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 6
---
## Merging branches
If branch happens, then change happens. You are going to want to incorporate the work from your separate branch back into your main line of development. `git merge` and `git mergetool` are two tools to deal with the consequence of a branch being so easy to do!

Typically **main** is the branch designated to accept all merges, but YMMV. A merge results in a commit that has two+ parent commits.

## Commands in Play 
* git merge
* git checkout [main]
* git diff main…bugfix  -> § see below
* git diff —name-status main…bugfix -> §§
* git log -1 -> §§§
* git merge —abort
* git config

> The output from `git diff main...bugfix` shows the difference between branches relative to when they became different. It’s a preview of what merge will do. The order is _significant_ for it: "main" is listed first and appears on top (“the highway”), bugfix is listed second (“the on-ramp”).

{{< figure src="day6-01.png" caption="Elementary fix, dear Watson. Don’t divide by zero in bash script 'baz'." numbered="false" >}}

> This command is overkill,in the example, but it demonstrates that bash script ‘baz’ (from bugfix) will be merged into main by the identifying glyph ‘M’. For large repositories, this command gives a useful summary of the actions that will be performed on `merge`.

{{< figure src="day6-02.png" caption="`git log -1` on the CLI." numbered="false" >}}

> Another sampling of “what was done” (after `git merge`).
At the CLI, we have the SHA1 IDs that made up the merge commit. It’s the same in `gitk`, maybe a little easier to interpret\see.
 
{{< figure src="day6-03.png" caption="GITK does not lack for the same info. See also the node connectors: color:red==main branch and color:blue==bugfix branch." numbered="false" >}}

## 10.3.1 Dealing with merge that needs human
Now we will refresh\restart and append a `printf` statement to bash script ‘baz’ on branch main. Nothing has changed on branch bugfix. But we cannot auto-merge them via the tools.
```
Auto-merging baz
CONFLICT (content): Merge conflict in baz
Automatic merge failed; fix conflicts and then commit the 
result.
```
Having gotten this error, bash script ‘baz’ on branch main has been altered, and it was altered with the glyphs denoting the local change `<<<<<< HEAD` and the remote change `>>>>>> bugfix`. We can see what happened and adjust bash script ‘baz’ to take the preferred code.

{{< figure src="day6-04.png" caption="Bouncing the conflicted merge thru VS Code (not shown) was an interesting, but mid-to-heavyweight action." numbered="false" >}}

## 10.3.4  Aborting a merge
_Short\Easy mode:_ If you are mid-merge and in a moment of realization that you have selected incorrectly, you can perform a `git diff` to see the conflicted hunks and abandon it via `git merge --abort` if necessary.
Chap 16 covers revert, or to take back, a merge.

## 10.4 Performing fast-forward merges
_Definition:_ The [fast-forward merge](https://www.google.com/search?q=git+diagram+fast-forward&tbm=isch&ved=2ahUKEwi8zYD83971AhVNYDUKHZIcC6wQ2-cCegQIABAA&oq=git+diagram+fast-forward&gs_lcp=CgNpbWcQAzoFCAAQgAQ6BAgAEB46BggAEAgQHjoECAAQGFCxGVilImDsI2gAcAB4AIABO4gB2QOSAQE5mAEAoAEBqgELZ3dzLXdpei1pbWfAAQE&sclient=img&ei=TUj5YfzyHM3A1QGSuazgCg) takes effect when the target branch is a descendant of the branch that it will merge with.
/Once Git detects that the branch being merged is a direct descendent of the current branch, it moves the local branch up on the remote branch–a fast forward to `main`!/

## 10.6.2 Changing how conflicts are displayed (merge.conflictstyle)
Enable this configuration (using `git config`) to subtly change the way conflicting hunks are displayed in a file.

## Performing octopus merges
An **octopus merge** is a merge that consists of more than two parents.

## References
[How to use VS Code as your Git editor, difftool, and mergetool](https://roboleary.net/vscode/2020/09/15/vscode-git.html)  
/I had not configured a difftool nor mergetool in `~/.gitconfig` The blog post, above, ☝️ was a useful reference. I briefly considered using graphical comparison tool (i.e. bcomp4), too!/  
[HOW TO RESOLVE CONFLICTS from git merge command documentation](https://git-scm.com/docs/git-merge#_how_to_resolve_conflicts)  
[octopus-merge README.md](https://github.com/seflaherty/octopus-merge)  
Kindly forked from code ocelot ☝️. This README as explainer for "famous octopus merge".
