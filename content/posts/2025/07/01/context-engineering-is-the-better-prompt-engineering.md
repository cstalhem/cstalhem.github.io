---
title: Context Engineering is the better Prompt Engineering
draft: false
date: 2025-07-01T20:22:00.000Z
summary: The term Context Engineering describes the "art and science" of the
  actual work better than "Prompt Engineering"
toc: false
readTime: true
autonumber: false
hideBackToTop: false
categories: Notes
tags:
  - Context Engineering
  - Simon Willison
  - Generative AI
  - Andrej Karpathy
  - LLMs
showTags: true
---
Simon Willison writes on [his blog](https://simonwillison.net/2025/Jun/27/context-engineering/#atom-everything) that he is warming to the idea of using the term **Context Engineering** in favour of Prompt Engineering.

As he writes himself on why Prompt Engineering is falling out of favour:

> Unfortunately, most people's inferred definition is that it's a laughably pretentious term for typing things into a chatbot!

I've started noticing that, especially when coding with agents, it is incredibly important to make sure you prime the agent with the information you want it to use for solving a task. Just giving a good, clear, instruction is not enough. I've had issues expressing this concept though, and Context Engineering seems to me that it fits the bill well.

Andrej Karpathy is also positive to this. He writes in [a tweet](https://x.com/karpathy/status/1937902205765607626):

> People associate prompts with short task descriptions you'd give an LLM in your day-to-day use. When in every industrial-strength LLM app, context engineering is the delicate art and science of filling the context window with just the right information for the next step.

Turns out, making LLM-powered applications is quite non-trivial if you want them to thrive in a production environment.
