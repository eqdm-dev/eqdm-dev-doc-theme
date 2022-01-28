---
title: Day 4
linktitle: Day 4
type: book
date: "2021-03-26T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---
## The time machine that is Git
These commits are incremental and ultimately _building something_. As time passes, you will have something to teleport back to (and once you have gotten that sample-that elusive nugget of data-and then go back to the present).

## Commands in Play
```
git log —parents
git log --parents --abbrev-commit
git log --oneline
git log —patch
git log —stat
git log —patch-with-stat
git help commit # then `/DISCUSSION` to skip ahead to the value of extended commit messages
git rev-parse HEAD # `git rev-parse` translates branch names to their corresponding SHA1 IDs
git rev-parse master
git checkout _short-SHA1-fragment_ # Go back to that version, results in "detached" HEAD!
```

> Note: checking out '$short-SHA1-fragment'.   
> You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by performing another checkout.
 
> If you want to create a new branch to retain commits you create, you may do so (now or later) by using -b with the checkout command again. Example:   
>   git checkout -b new_branch_name  

```
git commit -m "head of message" -m "this is another line" -m "still got more to say"
git rev-parse main~3
git show main@{3}
git show main^^^
git rev-parse :/"$some-commit-string"
```
{{< figure src="day4-01.png" caption="Display of the relationships via the SHA1 fragments between commits in `git log —parents —abbrev-commit`" numbered="false" >}}

{{< figure src="day4-02.png" caption="GITK tool launched via CLI. Commit history, SHA1 IDs, and DIFF shown as a graph in a GUI." numbered="false" >}}

{{< figure src="day4-03.png" caption="Although the Working area no longer contains a file named 'bad_calculator.py’, the instances of it in the commit history can be displayed to the person browsing the repo." numbered="false" >}}

## Test Your Knowledge
Q. How can you list the history from the first commit to the last?
What do you think is faster for Git to generate: the default listing or a reverse listing?
{{< figure src="day4-04.png" caption="This is a compact and full history of that weeks’ activity on the git-mol-buildtools repo." numbered="false" >}}

Q. Is there a way to list just the most recent _N_ commits? (Where _N_ can be any number?) How?  
A: Use `-<n>` to show only the last n commits.

Q. Can you display the date as time relative to the current time (for example, 2 hours ago)?  
A: Git log can take the time-limiting options such as `—since` and `—until `. E.g. `git log —since=2.weeks`

Q. I’m a big fan of `git —oneline`, but it’s a shortcut. What is it a shortcut for?  
A: It is like `git —pretty=oneline --abbrev-commit` used together. [Refer to git-scm doc](https://www.git-scm.com/docs/git-log).

## 8.5.3 Test Your Knowledge → Using other names
Q. What commits do each of these commands point to?  
A: `git rev-parse HEAD` points to the child SHA1 ID of main.

Q. What did the last git rev-parse search to find its commit?  
A: It searched commit messages.

Q. Does git rev-parse work on tag names?  
A: `git rev-parse $your-tagname` did not appear to work.

Q. Do these symbols (~3, @{3}, and so forth) work on tag names?  
A: `git show $your-tagname^` took me to the SHA1 ID commit for that tag.


## More Resources
[SHA1 IDs and computing collisions](http://marc.info/?l=git&m=111365428717118&w=2)  
[Subtlety of origin\HEAD in a clone](https://stackoverflow.com/questions/4359099/git-branch-named-origin-head-origin-master)  
