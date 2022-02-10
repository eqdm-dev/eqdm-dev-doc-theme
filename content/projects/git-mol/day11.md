---
title: Day 11
linktitle: Day 11
type: book
date: "2021-04-20T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 11
---
## Software archaeology

### Commands in Play
* git log
	* git log --parents -> Show the merging of branches
	* git log --parents --oneline
	* git --no-pager log <SHA1 ID fragment> -n 1 -> Select the merge commit entry, without pagination
	* git log --merges -> See only commits with merges in them
	* git log --oneline <repo-filename> <repo-filename>
	* git log --since 04/10/2021 --until 04/20/2021
	* git log --author=“<authorname | gmail.com>”
	* git log --stat HEAD^..HEAD -> Display the # of files that have changes between the most current (`HEAD`) commit and its immediate predecessor (`HEAD^`)
	* git log --patch -> Show the contents that have changed
```
	$ git log --patch 9b6dd3^..9b6dd3
	commit 9b6dd3e7ac029ff9df376d9a0950794d3a735be9 (HEAD -> main, tag: four_files_galore)
	Author: Sean Flaherty <sean@seanflaherty.com>
	Date:   Tue Apr 20 17:41:56 2021 -0400

	    Adding four empty files.
```
> NB. The use of the caret before the SHA1 ID indicates that you want tto display what changed between the most current commit (HEAD) and its closest predecessor (HEAD^).
* git shortlog -> Show just the short (<=50 char) commit message
	* git shortlog -e -> just the author list with email address
* git name-rev
* git grep
* git show
* git blame

{{< figure src="day11-05.png" caption="Output from `git log --graph --decorate --oneline branch_03` restricts the outlet from BASH script make_lots_of_branches.sh to a particular tag." >}}

Output from `git log --graph --decorate --oneline  —all` is productive, but not particularly special. But see next terminal cap 👇/

{{< figure src="day11-06.png" caption="Output from `git branch -r --contains ce051a3` shows that this branch is part of remote branch origin/new_feature. The switch `--contains` is useful to `git branch` when you are given a SHA1 ID and want to know what branch it belongs to." >}}

{{< figure src="day11-07.png" caption="Output from `gitk --all` is overwhelming from the perspective of a moderately actively-branched repo." >}}

{{< figure src="day11-08.png" caption="Output from `gitk branch_03 branch_10 main` is condensed for your perusal. You can also call up gitk with a single file as argument to see the history of that one file." >}}

{{< figure src="day11-09.png" caption="Output from `git gui blame math.sh`. I don't think I get it…." >}}

The `git notes` command is another helpful feature that lets you attach arbitrary notes to Git commits. In Git, after you make a commit, you freeze the commit log message along with the change into your repository’s timeline. But let’s say a bug was identified as originating from this particular commit. You could attach a short note to the commit that states this fact, without changing the commit itself. Think of git notes as yellow sticky notes for your commits.

```
	$ git log -n 2
	$ git notes add -m "no idea for note" 0614a5
```

{{< figure src="day11-10.png" caption="Output from gitk shows a small square box indicating the note!" >}}

```
	$ git notes edit 0614a5 # an edit was done...
	$ git --no-pager log 0614a5
	commit 0614a5e75b65d8a97504f9f5354fd4459ba95a12
	Author: Sean Flaherty <sean@seanflaherty.com>
	Date:   Wed Apr 7 23:24:44 2021 -0400

	    Adding printf.

	    This is to make the output a little more human readable.

	    printf is part of BASH, and it works just like C's printf()
	    function.

	Notes:
	    no idea for note
```
_Opens in editor, allowing me to correct the misspelling_
