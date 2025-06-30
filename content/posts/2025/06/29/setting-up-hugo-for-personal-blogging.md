---
title: Setting up Hugo for personal blogging
draft: false
date: 2025-06-29T22:46:00.000Z
summary: Description of how I set up my new blog. Migrating from MkDocs to Hugo.
categories: ["Homelab"]
toc: true
readTime: true
tags:
  - Blog
showTags: true
---

I decided I wanted something different than MkDocs to run my blog, mainly because I did not like the look of the theme I was using with MkDocs, but I also wanted a proper CMS so that I didn't have to worry about placing and naming files correctly myself.

Below is a breakdown of the process.

## Selecting a new engine

The initial work was simply to select which other engine I'd like to switch to. I worked with Claude Opus 4 and Research to figure this out.

I asked for an engine that was mature, would let me select themes and have a CMS so that I don't have to work with manually moving and naming files in a hierarchy. I also wanted to be able to host it on GitHub pages since that is free and simple, and won't require me to open any of my HomeLab services to the internet.

The recommendations came back as either [11ty](https://www.11ty.dev) or [Hugo](https://gohugo.io), and to use either Sveltia or DecapCMS. I initially went with Sveltia, but hav switched multiple times since it's a one-line modification to the docs to do it and they are interchangeable.

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

Run the command below in the directory and everything is setup more or less automatically.

```bash
hugo new site .
```

I'd have liked to use the flag `--format yaml` in order to get the config file setup in YAML format directly. I switched this later to yaml manually by creating a new hugo.yaml file next to the toml one and converting the syntax.

Installing the PaperMod theme was straightforward by using the [official installation guide](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/). I used the recommended method of adding a Git submodule.

### Installing Decap CMS and Authenticating

Again, I followed the official guide, this time from [here](https://decapcms.org/docs/install-decap-cms/).

The thing that took the most time was to setup the authentication based on GitHub. The official guide was not possible to use since I did not want to use Netlify. Sveltia provides a simple guide to set up authentication using Cloudflare instead, using [this repo](https://github.com/sveltia/sveltia-cms-auth).

I followed that process, but instead of using an OAuth app, I switched to a regular GitHub App based on the information in [this issue](https://github.com/sveltia/sveltia-cms-auth/issues/15).
I initially used the wrong fields to set my variables in the Cloudflare so it did not work properly on the first go.

### Configuring Hugo, PaperMod and Decap CMS

The current config I have can be found here:

- Hugo/PaperMod: [hugo.yaml](https://github.com/cstalhem/cstalhem.github.io/blob/6a3d833636bc1b54b60b0e326636a772ac1d0a2b/hugo.yaml)
- Decap CMS: [config.yaml](https://github.com/cstalhem/cstalhem.github.io/blob/6a3d833636bc1b54b60b0e326636a772ac1d0a2b/static/admin/config.yml)

## Issues along the way

**Posts not being built properly**
Initially, my posts we not being built properly and I was unable to understand why. After a while I decided to use Claude Code to try to figure it out, which was great. It analysed the codebase and the docs (using the Context7 MCP and web search) and figured out that I had an issue with the `slug` and `path` setting in my Decap CMS config file. Once I got rid of the `slug` setting completely (and included it in the `path` instead), everything worked perfectly.

**Setting up Tags and Categories**
Each of my posts currently can accept a single category and multiple number of tasks. In order to get a nice auto-complete for these (to make it simpler to use and prevent typos from creating duplicate tags), I had to setup these as their own Collections in Decap CMS. I then had to use a `relation` widget to refer to them in the Posts collection.

Here is an example of my Tags collection:

```yaml
- name: "tags"
  label: "Tags"
  label_singular: "Tag"
  create: true
  folder: content/tags
  path: "{{slug}}"
  fields:
    - { label: "Name", name: "name", widget: "string" }
```

This caused another problem though. Each time I created a new tag or category, these were shown on the home page, but without any content (as I currently only have a `name` property). In order to fix it, I had to add this to my `hugo.yaml` config:

```yaml
params:
  mainSections: ["posts"]
```

The last fix was discovered by Claude Code on it's own once I asked it to analyse my code and try to fix this by using the relevant parts of the Hugo docs.
