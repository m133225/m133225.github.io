---
layout: post
title:  "Comparison processes between open-sourced projects"
date:   2016-03-31 12:00:00 +0800
categories: process
---
Since open-sourced projects have different contributors and background, the workflow they have put in place are rather different. For example, open-sourced softwares which involve people without much software engineering experiences will tend to have less prominent process, and may tend to repel new contributors as they don't know where or how to start.

In this post, I will be comparing the processes between my projects and extract out the good points.

__HubTurbo__  
_Setting up_

Setting up of HubTurbo is rather straight-forward.
There are step-by-step instructions available in the repository.

However, if there are bugs, the new contributor might become helpless since he or she might not have the technological expertise to do it in the first place.

_Contributing to HubTurbo_

1. First off, new contributors are required to submit a `forFirstTimers` issue to make sure they know the basic contribution workflow. This usually involves 1-line changes (or even 1-word changes!).
2. Contributors are usually free to choose their subsequent issues. However, they are usually recommended to avoid making new suggestions until they are familiar with several aspects of the project.

_Reporting Issues_

HubTurbo has a rather flexible issue reporting workflow. Whenever a developer or an user has found an issue, he or she is free to create the issue. It is up to the developers to accept or reject the issue, but they are usually accepted as long as they are reasonable. Of course, it is still encouraged that the person who reports the issue to comprehensive;y address the issue.

_Submitting Pull Requests_

1. Before submitting PRs, HubTurbo encourages the contributor to read through the contribution guidelines, to make sure they know of the coding style & testing requirements.
2. It is also usually a requirement that PRs do not decrease test coverage, unless there are valid reasons.
3. During its active periods, there will be weekly releases, in addition to weekly meetings to discuss the problems encountered and the direction that HubTurbo should go towards. Each active member is also required to submit at least one PR for each release (preferably more).
4. Due to the weekly releases, its developers are rather active, and PRs submitted will usually be attended to or reviewed quickly.

__Atom__  
_Setting up_

Instruction for setting up atom may not be that obvious to a new contributor:
Key instructions are found [here](http://flight-manual.atom.io/getting-started/sections/installing-atom/) instead of the contribution guidelines of the repository.

Moreover, since atom is modularized, the user may not know how to set-up the repository he wishes to contribute to.
For example, the user wishes to contribute to the tree-view package but simply cloning it will not suffice. The user has to link the cloned repo to the main repo, so the main repo will include the package during its run. This is indicated [here](https://github.com/atom/atom/blob/master/docs/contributing-to-packages.md) which is not that obvious to a new user since it is not linked from anywhere.

_Contributing to Atom_

It is rather similar to HubTurbo process in the aspect of coding styles guidelines (for CoffeeScript/Javascript/CSS).

There is a minor difference: While atom has `beginner` issues, contributors are NOT required to submit a `beginner` issue before going on to more complicated ones.

_Reporting Issues_

Atom, however, has a good process for reporting issues. They have a structured checklist to minimize already-reported issues and encourages the users who report to include reproduction steps. Of course, this isn't always possible.
This checklist includes stuff like the OS information, atom version, whether the problem is reproducible in atom safe mode, whether the user has went through the existing list of issues, and so on.
This is a process that may take up a significant time if a user wants to report an issue, which may in turn frustrate the user till he or she no longer wants to make an issue. While it may be so, it is still a good form of documentation so that contributors can ensure that they have a good overview of the problem. In addition, if the user 'gives up' reporting that easily, maybe he or she won't make a comprehensive issue anyway :p

_Submitting Pull Requests_

1. Similarly to HubTurbo, atom encourages the contributor to read through the contribution guidelines.
2. The only requirement before a PR can be merged is that it compiles on Travis/AppVeyor. Whether a PR decreases its test coverage does not matter, and is entirely up to the developer reviewing the PR.
3. Unlike HubTurbo, it does not have scheduled releases. It is up to the developers to merge a couple of PRs, then 'release' them as a new minor version. (e.g. 1.7.0-beta2) The duration for a minor version ranges from a few hours to a few days.
4. However, there are many lingering PRs that `needs-review` but are not looked at even after the contributor has addressed the problems identified. (There are even 2 year-old PRs!) This could be due to the lack of developers, and they can only address problems that are of high priority.
