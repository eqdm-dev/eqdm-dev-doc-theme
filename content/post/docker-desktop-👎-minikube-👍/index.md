---
title: Docker Desktop 👎 | Minikube 👍
subtitle: Changes in Personal Docker Desktop has made it untenable. So, I am moving on.
date: 2021-10-13T00:29:13.694Z
summary: Changes in Personal Docker Desktop has made it untenable. So, I am moving on.
draft: false
featured: false
tags:
  - Containers
  - Computarse
  - Windows10
categories:
  - Infrastructure
image:
  filename: ""
  focal_point: ""
  preview_only: false
---
## Pre-requirements for this PC 🖥
- Hyper-V
  - Activated by the means of so doing
  - Consider adding your user to the Windows group of Hyper-V Administrators for better allowances on the terminal sessions
    - 🙋‍♂️ Start at Windows Administrative Tools > Computer Management > System Tools > Local Users and Groups > Groups > Hyper-V Administrators 
- Minikube
  - Available via `winget` 🙌
  - `winget install --id Kubernetes.minikube`
- Kubectl
  - Downloaded and put on Windows Path 💔
  - [Atomic Commits: Everything Useful I Know About kubectl](https://www.atomiccommits.io/everything-useful-i-know-about-kubectl)
  - [Overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)
  - [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- Docker CLI
  - Downloaded and put on Windows Path 💔
- Git and Git CLI
  - `winget install --id Git.Git`
  - `winget install --id GitHub.cli`
## Optional
- Winget
- Windows Terminal
  - Git-Bash in Windows Terminal (it's easy, really!)
## Starting Goals
- Transition to using Minikube and it's built-in docker daemon without much disruption
- Let's continue to be 🙅‍♂️on additional VMs
- Let's keep projects `KinD` and `K3d` "on hold/watching" status
- And the same with projects `buildah` and `podman`
## Doing It
- Run `minikube start --driver hyperv`
  - Consider tuning parameters for CPU and memory limits e.g. `minikube config set {cpus|memory} {quantity}` 
- Run `minikube docker-env --shell {bash|cmd|powershell}`
  - 🙋‍♂️ This command gives you the information needed for Docker CLI and this info is provided. To omit the `shell` flag however means that the shell will be guessed, so you may be given a subsequent command to run that will produce error. Moreover, `shell  powershell` will be incorrect for `pwsh`, so maybe not run that Terminal session for now.
  - Bash: `eval $(minikube -p minikube docker-env)`
  - CMD: `@FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env') DO @%i` 
  - ☝️ 🎁 *Protip: Use a better shell*
  - Powershell: `& minikube -p minikube docker-env | Invoke-Expression`
- `docker container ls`
  - 🔗 Docker Client and Server 🎉



