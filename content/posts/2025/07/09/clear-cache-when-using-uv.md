---
title: Clear cache when using uv
draft: false
date: 2025-07-09T10:03:00
summary: If using uv as the package manger with python, it might be worth clearing the cache once in a while.
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: TIL
tags:
  - Simon Willison
showTags: true
---
Originally from Simon Willison, who had 30+ GB of space cleaned up from his hard drive by running this:

```zsh
uv cache prune
```

In my case, I cleaned out 1.5GB in total.

Apparently, uv is smart enough to figure out on its own what to keep in the cache and what can be deleted.
