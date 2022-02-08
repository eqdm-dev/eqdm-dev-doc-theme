# Git in a Month of Lunches - day 10
---
title: Day 10
linktitle: Day 10
type: book
date: "2021-04-19T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 10
---
## Keeping in sync

### Commands in Play
* git pull -> Sync local repo with an upstream repo. It is really two commands: git fetch and git merge
* git fetch -> The first part of git pull
* git merge FETCH_HEAD -> Merge new commits from FETCH_HEAD into the current branch
* git pull —ff-only -> Merge only if FETCH_HEAD is a descendant of the current branch (a fast-forward merge)
* git branch —set-upstream-to=origin/main -> This would be a reset to your local branch to be based from its origin clone (but you can imagine that you may go elsewhere at an as-needed basis)

It’s all about `git pull`, which is compromised by two commands: `git fetch` and `git merge`

{{< figure src="day10-01.png" caption="A snapshot looking at the math.git repo at owner 'Carol'. Another dev has pushed a change to math.git so that Carol's local is out of date." numbered="false" >}}

* The merge is the more substantial operation. It’s much more complicated than `git push`. When changes can be cleanly merged, `git pull` is just the mirror operation of `git push`. Anything more complicated, and you have to make the merge in a local repository and then push the result.
* Consider this sentence from the `git pull` help page: "In its default mode, `git pull` is shorthand for `git fetch` followed by `git merge FETCH_HEAD`."
	* So `git fetch` retrieves references, this means branches or tags.
	* When the references arrive at the local repo, they are laid down on top of it, along with any files that they point to.
	* These references are tracked by using remote-tracking branches.

{{< figure src="day10-02.png" caption="A snapshot looking at the math.git repo at owner 'Carol'. The command flag `--decorate` provides a list of the SHA1 IDs and the **references** (shown in parentheses, like this 😉). Remote references are prepended with `origin/`. The label HEAD is your git playback machine, and it is always pointing to your current branch." numbered="false" >}}

NB. The state of Carol’s repo ☝️ is _after_ the `git pull` from the main branch `math.git`. See how the SHA1 ID `080a405` is now the HEAD and it has a reference to `origin/`. This was a "clean merge" of the repos and the complexity was wrapped by that `git pull`.

{{< figure src="day10-03.png" caption="The View definition in gui app ‘gitk’ allows you to show all local and remote branches." numbered="false" >}}

{{< figure src="day10-04.png" caption="App GITK showing the history, with labels for the remote tracking branches on top." numbered="false" >}}

### git fetch > git pull 

{{< figure src="day10-05.png" caption="In the terminal from Carol's repo, we done a `git fetch`. The remote-tracking branch (SHA1 ID: 6fead5c) is ahead of the local HEAD (SHA1 ID: 08a405)." numbered="false" >}}

So to consider the actions of `git pull` at a step-wise basis, access the remote master branch in Carol's repo via: `git rev-parse origin.main`.

- ☝️ That latter command will give you the same SHA1 ID as FETCH_HEAD!

You still have two commit IDs, see what is different between these two branches by entering: `git diff HEAD..FETCH_HEAD`.

- FETCH_HEAD is used as the argument to `git merge`.
- FETCH_HEAD is the reference to the remote branch that was previously fetched.

{{< figure src="day10-05.png" caption="Performing a git merge on the CLI opens up the default editor for the commit message. Note the comment that an empty message aborts the commit!" numbered="false" >}}

- ☝️ Performing the git merge results in a Fast-Forward to the local branch!


