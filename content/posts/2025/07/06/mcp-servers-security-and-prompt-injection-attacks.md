---
title: MCP servers, security, and prompt injection attacks
draft: true
date: 2025-07-06T14:21:00
summary: Notes on when an MCP-servers can be used by attackers to get access to private data
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: Notes
tags:
  - MCP
  - Simon Willison
  - LLMs
  - Model Context Protocol
  - AI Agents
  - Test tag
  - Prompt Injection
  - Security
showTags: true
---
Simon Willison has coined (as far as I am aware) the term ["The lethal trifecta"](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta) noting the dangers of when an MCP server can be used by an attacker to easily exfiltrate data from a private source.
## The three parts
The three parts of the lethal trifecta for an MCP are:
1. Access to private data
2. Exposed to untrusted input
3. Ability to communicate externally

### Access to private data
Access to private data
