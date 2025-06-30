---
title: Setting up Hugo for personal blogging
draft: true
date: 2025-06-29T22:46:00.000Z
categories: Homelab
tags:
  - Blog
---
I decided I wanted something different than MkDocs to run my blog, mainly because I did not like the look of the theme I was using with MkDocs, but I also wanted a proper CMS so that I didn't have to worry about placing and naming files correctly myself.

Below is a breakdown of the process.

## Selecting a new engine

The initial work was simply to select which other engine I'd like to switch to. I worked with Claude Opus 4 and Research to figure this out.

I asked for an engine that was mature, would let me select themes and have a CMS so that I don't have to work with manually moving and naming files in a hierarchy. I also wanted to be able to host it on GitHub pages since that is free and simple, and won't require me to open any of my HomeLab services to the internet.

The recommendations came back as either [11ty](https://www.11ty.dev) or [Hugo](https://gohugo.io).

I also got a complete migration guide together with a checklist.

I can't share the full conversation since it uses the Research mode.

## Converting from old to new setup

### Installing Hugo & PaperMod

Before beginning, a new branch was created to allow me to wreck everything if necessary:

```bash
git checkout -b hugo-migration
```

The rest turned out to be relatively straightforward.

#### Clean out everything in the repo that is not Git related
I did this manually by just `rm -r [folder-name]` or `rm [file-names]` to keep it simple.

#### Install Hugo on my machine
Since I'm on a Mac, using homebrew is the simplest solution:

```bash
brew install hugo
```

#### Setup a new blog
Simply run `hugo new site .` in the directory



### Installing Decap CMS and Authenticating

### Configuring Hugo & PaperMod

## Issues along the way

* Setting up GitHub App instead of OAuth App for better scoping of permissions
* Posts not being built properly (slug/path mismatch?)
