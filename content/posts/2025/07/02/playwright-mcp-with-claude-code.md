---
title: Playwright MCP with Claude Code
draft: false
date: 2025-07-02T09:43:00
summary: Installing and using the Playwright MCP with Claude Code
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: TIL
tags:
  - Claude Code
  - Generative AI
  - Simon Willison
  - Model Context Protocol
showTags: true
---
Today on [Simon Willisons blog](https://simonwillison.net/2025/Jul/1/using-playwright-mcp-with-claude-code) I read about how to use the **Playwright** MCP-server with Claude Code.

Generally, setting up MCPs with Claude Code is easy, but there are a few things I still am not familiar with, such as what the difference between using `npx` to run a server and installing it as an npm package and use `npm run` is.

Playwright seems to be a particularly useful MCP since it allows Claude Code to run a browser window it can control, and that I myself can see and interact with. It's based on Chrome.

It will be immensely useful for me when working on the look of this blog for example.

## Installing Playwright in Claude Code
To get up and running with Playwright, it's enough to do this:

```zsh
claude mcp add playwright npx '@playwright/mcp@latest'
```

With this type of MCP that might be relevant in many projects, this section from the [Anthropic documentation](https://docs.anthropic.com/en/docs/claude-code/mcp#choosing-the-right-scope) on Claude Code is useful:

> **Choosing the right scope**
>
> Select your scope based on:
> - Local scope: Personal servers, experimental configurations, or sensitive credentials specific to one project
> - Project scope: Team-shared servers, project-specific tools, or services required for collaboration
> - User scope: Personal utilities needed across multiple projects, development tools, or frequently-used services

So, I'd add the `-s user` flag as well to scope to my user instead of Local/Project:

```zsh
claude mcp add playwright -s user npx '@playwright/mcp@latest'
```
