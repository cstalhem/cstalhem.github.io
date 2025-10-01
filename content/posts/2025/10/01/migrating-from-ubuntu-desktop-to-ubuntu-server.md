---
title: Migrating from Ubuntu Desktop to Ubuntu Server
draft: true
date: 2025-10-01T09:17:00
summary: ''
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: Posts
tags:
  - Homelab
  - ZShell
  - pi-hole
  - Homebrew
  - dns
  - Ubuntu
showTags: true
---
My Ubuntu version (24.10) was not an LTS-version and updates stopped recently.

I had considered moving from the Desktop version I currently used, to the Server version since I am currently using the device as a server anyway, so this seemed like a good opportunity.

Here are the steps I took and how I did it:

# Planning

I needed to do the following things before reinstalling Ubuntu:

1. Backup configuration
2. Backup Docker Compose files
3. Ensure GitHub Actions keep working
    1. Back up the Public Key used to deploy to the machine
    2. Recreate the service account that deploys the relevant data

# Backup Configurations

The relevant users for backing up configuration are:

1. Main user
2. Service account

## Main user

The main user uses Z-shell and Oh-my-zsh, so these needs to get installed on the new machine. Also, the .ssh folder needs to be retained in order to make it simple to keep SSH and other access retained as easily as possible. Fastfetch as well as `gh` needs to be installed and their configs moved.

In summary, these folders/files need to be backed up:

- `~/.zshrc`
- `~/.ssh`
- `~/.config/fastfetch`
- `~/.config/gh`
- `~/docker`

# Backup Docker

Since we already backed up the `~/docker` directory in the previous step, we should be good to go with everything Docker.

We do, however, need to reinitialise all images and containers, and some of the images need to be reconfigured through their GUI:s in order to get everything running again.

# GitHub Actions

TBD
