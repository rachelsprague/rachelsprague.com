---
layout: post
title: "Stop Repeating Yourself to Your AI Agent"
date: 2026-03-23
body_class: blog-post
subtitle: "Stop Repeating Yourself to Your AI Agent"
tags: [tools, ai, workflow]
---

AI pair programming is everywhere in tech right now. Everyone's using it, everyone's figuring it out.

---

### **A Little Context**

I'm a senior data analyst. I work mostly in dbt, SQL, and Git. I've been using AI coding assistants heavily for the past year and have tried most of the major models. Lately I've been on Claude (who isn't, amirite?).

Bad code in a data pipeline might silently corrupt downstream reports for weeks before anyone notices. That caution that comes with data has been one of the more important things to communicate to an agent.

---

### **What I Noticed**

I found myself repeating myself while working with agents. Don't deploy yet. Let me validate first. Don't assume the existing logic is correct. Show me what you're changing before you change it.

Providing context to an agent is crucial.

---

### **The AGENTS File**

Most AI coding tools support some version of a persistent instructions file — a markdown file that lives in your repo and gets loaded into the agent's context at the start of every session. Call it `AGENTS.md`, `.cursorrules`, whatever your tool supports. Same idea.

I started one. Actually, I asked Claude to make one for me. And I updated the file as I would think of more context.

The file lives in the repo, which means it's version controlled.

---

### **Using AI to Audit Itself**

I asked the agent to review our conversation (or conversations, if your agent has the memory) and identify patterns:

* Things I consistently pushed back on
* Corrections I made more than once
* Preferences that I repeated

It surfaced things I hadn't consciously noticed myself doing. It validated that I consistently insisted on validating and adding this to the AGENTS file was the right move.

Now that's in there. Next session, the agent already knows.

---

### **Why This Matters for Data Work Specifically**

An agent will optimize for shipping. That's fine for a lot of work. For data work, I'd rather it optimize for correctness and visibility — show your work, flag assumptions, don't touch what we're not changing.

Those aren't hard rules to follow. But the agent won't follow them consistently unless you tell it to, and it won't remember you told it unless it's somewhere persistent.

The AGENTS file is just a way of encoding how you work so you're not re-explaining yourself every day.

---

### **Tools & Skills**

- AI-assisted development
- Prompt engineering
- dbt / SQL
- Git
- Workflow design

---