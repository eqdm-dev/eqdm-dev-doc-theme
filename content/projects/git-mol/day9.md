---
title: Day 9
linktitle: Day 9
type: book
date: "2021-04-09T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 9
---
## Pushing your changes

## Commands in Play
* git push origin master -> From math.github to remote github.com/rickumail/math is Error: 403 Denied
* git push origin main -> From math.carol to remote math.git is 'Everything' up-to-date
* git commit -a -m "my good, short comment" -> Add and commit in one line
* git status
* git log -2 -> View last two commits (Today, 4/9 and Weds, 4/7)
* git log -n 2 -> ☝️ in longer form
* git ls-remote origin
* git remote -v show origin -> Show a formatted, human output
* git checkout -b [new-branch-name] [main] -> Create new branch and switch to it
* git push --set-upstream [origin] [new-branch-name] -> This will be written into the configuration file, os you won’t need to repeat this command
* git config —set-regexp [search-string] -> Access the git config file searching/filtering for the [search-string]
* git config --global push.default [nothing | current | upstream | simple | matching] -> Refer to the git config documentation that sets what will happened when you push a branch. This prevents a push of a branch to remote that was not intended as a share.
* git ls-remote [origin] [:new_branch] -> From this local, delete the remote reference to new_branch

{{< figure src="day9-01.png" caption="The action of ‘push’ to a remote is a summary of all the compression and comparison of objects processed by git. The change of the SHA1-IDs is a very important bit of info. The SHA1-IDs are added to the local and the remote, too." numbered="false" >}}

{{< figure src="day9-02.png" caption="I have deleted the 'new_branch' at math.carol and a reference still exists to math.git, with a special switch `:new_branch` the reference can be removed." numbered="false" >}}

## Resources
[Git-SCM docs–git push](https://git-scm.com/docs/git-push)
_NB. Read the note about the Fast-Forwards section._  
_NB. Read about ref specs in the git-push help._  

[Git-SCM docs–git config](https://git-scm.com/docs/git-config)
_NB. Read about the section Files and the configuration setting in push.default._

