---
title: Day 3
linktitle: Day 3
type: book
date: "2021-03-25T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---
## Commands in Play
* `git diff`
* `git diff —staged`
* `git status`
* `git add -p`
```
╭─❯ ~/Documents/GitHub/git-mol-buildtools(main) ✘
╰─$ git add -p
diff --git a/README.md b/README.md
index 64b769a..dbc9800 100755
--- a/README.md
+++ b/README.md
@@ -11,5 +11,11 @@ TL;DR;

 a=1
 b=2
+#
  1 # Manual hunk edit mode -- see bottom for a quick guide.
+# These are for testing
+echo "\t a is $a"
+echo "\t b is $b"
+
 c="`expr $a + $b`"
-echo "\t ========== \n\t $c is the product of $a plus $b \n\t ========== "
+l="============================"
+echo "\t $l \n\t $c is the product of $a plus $b \n\t $l"
(1/1) Stage this hunk [y,n,q,a,d,s,e,?]? ?
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
```
☝️with `?` you get the explainer for those eight “mystery” switches. This command is _functionally_ a `git diff`.

## File Rename and Hunks
This begins with a “known bad” script–`bad_calculator.py`. It is functional, but soon enough came the bug report that it does the incorrect action for a tool that claims its a “simple calculator”.

Before making the changes, lets no longer call the script by that name…
/Note: The file is checked in to the `git-mol-buildtools` repo already./
1. On the CLI: `mv bad_calculator.py simple_calculator.py && git status`
	* git status shows that two actions have been seen, you deleted `bad_calculator.py` and now have as an untracked file `simple_calculator.py`
2. On the CLI, remove the “known bad” script `git rm bad_calculator.py`
	* A follow-up `git status` shows that those two actions are now understood by Git as a rename action to be committed to the repo  
3. Now commit the change to the file name
	* Note: `git mv` will combine the ☝️actions
4. Next, make the several changes to each of the four “known bad” actions in `simple_calculator.py` in your $favorite_editor and save it (the script is now changed in the Working area
5. Now, we will add each fix separately as a code hunk
	* Run `git add -p`
	* Hit `s` to split the changes into 4 code hunks
	* Hit `y` to stage the top-most hunk
	* Hit `q` to do no more
	* Do a `git commit -m` for the split hunk with a relevant message
	* Repeat until you have done them all for four total commits to the repo

{{< figure src="day3-01.png" caption="My Working area changes to `simple_calculator.py`." numbered="false" >}}

{{< figure src="day3-02.png" caption="A walk-thru of the `git add -p` actions on the CLI. One hunk is now in the Staged area and the remaining hunks are in the Working area." numbered="false" >}}

{{< figure src="day3-03.png" caption="See `git log` has recorded all the changes, atomically." numbered="false" >}}

## Side-by-Side capture

{{< figure src="day3-04.png" caption="Side by side with `git gui` (L) and `git diff` (R); notice how the number of hunks reported are fewer in the git view. See the `@@` symbols." numbered="false" >}}

## Lab
Working with multiple hunks… I don’t think I really understood this one well. Maybe it was wording, as in do you want me to a.) append the change file contents to the original or b.) copy/overwrite the other file and witness the changes between the working group and the initial commit?

Also, [RTFM](http://www.catb.org/~esr/jargon/html/R/RTFM.html) on:
* git checkout
	* `man 1 git-checkout`  -> git-checkout - Switch branches or restore working tree files
	* Shows ascii drawings of the tree with ‘DETACHED HEAD’
	* ~3300 words
* git reset
	* `man 1 git-reset` -> git-reset - Reset current HEAD to the specified state 
	* ~2800 words

