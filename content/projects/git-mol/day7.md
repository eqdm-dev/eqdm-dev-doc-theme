---
title: Day 7
linktitle: Day 7
type: book
date: "2021-04-07T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 7
---
## Cloning
_Definition:_ The act of making a physical copy of a git repository.  
Using the 'bare' directory as the centralized copy of local disk, we can clone from it for ‘Bob’ and ‘Carol’ (🤔 I guess you're ‘Alice’ in this scenario). Thus creating three copies of 'bare' repository. A 'bare' repository are what are hosted on GitHub or any Git server.

**Notes about Clones**
1. The clone has a special reference to the original repository. This reference lets your clone push (send) and pull (receive) changes to and from the original repository. 
2. Via `git branch`, the only branch that appears in the clone is the active branch (the one HEAD points to).

## Commands in Play
* git clone [source] [destination dir]
* git log —simplify-by-decoration —decorate --all --oneline
{{< figure src="day7-01.png" caption="Use this to get a simplified list of branches on the CLI." numbered="false" >}}
* git branch -> This is a simplified view between source and branch with the sole checked out branch.
* git branch —all -> This is a more complete view of branches in the remote repository (thus showing them within the clones, as well).
* git clone —bare [reponame]  [reponame.git]
	* File 'reponame.git' is not anything special. It’s a folder, just like the clone was… but since its a bare directory it does not have any "room" for a working directory. Being a bare directory means that it has no reference to the original repository. It is also a vital piece for collaboration via Git code sharing.
* git ls-tree HEAD -> it takes one argument: SHA1 ID, branch, or tag (note that all of these point to commits)

## 11.1.3 Checking out branches
A clone copies that entire repository, so that it has the files and the history it needs to re-creation and branch that existed in the original repository

`git checkout another_fix_branch`  

☝️ is short-form for this command that explicitly tells what\how Git will see it:

`git checkout -b another_fix_branch remotes/origin/another_fix_branch`  

{{< figure src="day7-02.png" caption="There are two references to '(branch) another_fix'. On the right, the line is solid indicating you’ve checked it out and HEAD is there at your local." numbered="false" >}}
