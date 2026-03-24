---
layout: post
title: "Adding an RSS Feed to a Jekyll Site"
date: 2026-03-24
body_class: blog-post
subtitle: "Two steps. That's it. One, two step. We about to get it on."
image: /assets/images/blog/2026-03-24/ss1.png
tags: [jekyll, tools, setup]
---

<div class="image-row">
  <img src="/assets/images/blog/2026-03-24/ss1.png" alt="RSS feed screenshot" style="max-width:50%;">
</div>

I didn't realize RSS feeds were still a thing, so (naturally), I wanted one. Turns out Jekyll basically does it for you.

---

### **Step 1 - The Plugin**

GitHub Pages supports `jekyll-feed` out of the box — no custom build step needed. Add it to `_config.yml`:

```yaml
plugins:
  - jekyll-feed
```

Push that and your feed is live at `/feed.xml`. Easy. Like Sunday morning.

---

### **Step 2 - Add It - Make It Discoverable**

Browsers and RSS readers look for a `<link>` tag in the page head to auto-detect feeds. Add this to the `<head>` of your layouts:

```html
<link rel="alternate" type="application/atom+xml" title="{{ site.title }}" href="/feed.xml">
```

Then add a visible link somewhere on the page — I put mine in the footer:

```html
<a href="/feed.xml">RSS</a>
```

---

### **Step 3 - Rejoice**

That's the whole thing. We did it, Joe.

---

### **RSS Readers**

It's been a long time since I've used an RSS Reader (RIP [Google Reader](https://en.wikipedia.org/wiki/Google_Reader)). Apparantly I already have a [Feedly](https://feedly.com/) account so I downloaded the app and am trying it out.

---

### **Tools & Skills**

- Jekyll
- GitHub Pages
- RSS / Atom
- `jekyll-feed` plugin

---