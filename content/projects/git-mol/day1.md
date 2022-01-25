---
title: Day 1
linktitle: Day 1
type: book
date: "2021-03-22T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## Overview
Intro to distributed version control (DVCS), intro to the CLI, intro to Git, installation of Git, configuration of Git.

## Intro to the CLI
Command-line editing, summarized:
| Command | Action                                 |
| ------- | :------------------------------------- |
| Ctrl-A  | Move cursor to the beginning           |
| Ctrl-E  | Move cursor to the end                 |
| Ctrl-U  | Delete all to the left                 |
| Ctrl-K  | Delete all to the right                |
| Ctrl-H  | Delete character to the left of cursor |
| Ctrl-D  | Delete character under cursor          |

## Intro to Git
Take a peek at what git commands are a few keystrokes away…
```
% git help -a
% git --paginate help -a // (szf) you may also sub `git -p…`
```

## Configuration of Git

```
% git config --list
core.symlinks=false
core.autocrlf=true
color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
pack.packsizelimit=2g
help.format=html
http.sslcainfo=/bin/curl-ca-bundle.crt
sendemail.smtpserver=/bin/msmtp.exe
diff.astextplain.textconv=astextplain
rebase.autosquash=true
user.name=Rick Umali
user.email=rickumali@gmail.com
gui.recentrepo=C:/Users/Rick/Documents/gitbook
gui.recentrepo=C:/Users/Rick/Documents/RUVW
```

## Lab
Q. You told Git your name and email, but where does Git save that information? See if you can locate where this is.  
A: It’s at the root of your `/home` folder; file `.gitconfig`.

Q. Git is known as the _stupid content tracker_. What git help page says this?  
A: It’s the first item of the `man page`.

Q. What is the Git command that forward-ports local commits?  
A: `git-rebase - Forward-port local commits to the updated upstream head`

Q. What does the abbreviation DAG stand for, in the context of Git?  
A: DAG is the abbreviation for **Directed Acyclic Graph**. It’s how Git tracks files within any given branch. It can be “viewed” like a network graph or a left-to-right branched structure.

Q. Does your installation come with a Git tutorial help file?  
A: Yes. `man git` (?)