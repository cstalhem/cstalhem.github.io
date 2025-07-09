---
title: The order of items in $PATH matters, and ZSH caches locations
draft: true
date: 2025-07-09T16:33:00
summary: When trying to update Git to the latest version using Homebrew, realised this when I didn't get the new git to work.
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: TIL
tags: []
showTags: true
---
Today I realised that the order of paths in the $PATH variable actually matters. Earlier items take precedence over later ones (which itself is counterintuitive for me...).
This means that if you want to add a new directory to the path,

```export PATH="/new/directory/location:$PATH"```
is not the same as
```export PATH="$PATH:/new/directory/location"```

This feels a bit obvious in hindsight, but I had not thought about it before.

I was going to install an updated version of Git, and since I'm on a Mac and like Homebrew as my package manager, I wanted to use it to manage git going forward since this makes everything nice and easy for me.
After running `brew install git`, my shell was not picking up git in the new location (`/opt/homebrew/bin/` since I have a Mac with Apple Silicon).

It turns out that ZSH actually caches the location of executables, so even though Homebrew came before the regular `/usr/bin/` in my PATH, the new Git executable was not picked up. However, there was a simple fix: running `rehash` reloads the locations and, presto, everything worked like a charm!
