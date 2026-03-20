---
layout: post
title: "Pulling the Latest Media from Bluesky into Your Site"
date: 2026-03-21
body_class: blog-post
subtitle: "Using the Bluesky public API to display your latest photo and video posts"
image: /assets/images/blog/2026-03-21/ss1.png
tags: [javascript, api, html]
---

I wanted to pull my latest photo and video posts from a Bluesky account directly into a page on my personal site. I didn't want to embed anything or use an iframe (do people still use iframes? Genuine question - I haven't used an iframe since 2002). Turns out Bluesky has a public API that makes this pretty straightforward.

---

### **What It Does**

- Fetches the most recent photo post from a Bluesky account
- Fetches the most recent video post from the same account
- Displays both inline on the page with links back to the original posts
- No API key required — Bluesky's public feed endpoints are open

---

### **The API**

Bluesky's public API is part of the AT Protocol. The endpoint I used:

`https://public.api.bsky.app/xrpc/app.bsky.feed.getAuthorFeed`

Key parameters:
- `actor` — the Bluesky handle
- `filter=posts_with_media` — limits results to posts that have media attached
- `limit=50` — how many posts to scan

No authentication needed for public accounts.

---

### **How I Got Here**

Started with just photos. That part was easy — the API response is clean and consistent for images.

Video was a different story. First issue: reposts were showing up in the feed and I only wanted original posts, so I had to filter those out. Second issue: Bluesky surfaces video under a few different `$type` values depending on how it was uploaded, so a single check wasn't enough. Took some digging through the raw API response in dev tools to figure out what was actually coming back.

The final version handles all of it.

---

### **The HTML**

Just two placeholder divs that JavaScript fills in:

```html
<h2>Latest Photo</h2>
<div id="latest-photo"></div>

<h2>Latest Video</h2>
<div id="latest-video"></div>
```

---

### **The JavaScript**

```javascript
async function loadBlueskyMedia() {
  const handle = "your-handle.bsky.app";
  const photoEl = document.getElementById("latest-photo");
  const videoEl = document.getElementById("latest-video");

  try {
    const res = await fetch(
      `https://public.api.bsky.app/xrpc/app.bsky.feed.getAuthorFeed?actor=${encodeURIComponent(handle)}&filter=posts_with_media&limit=50`
    );
    const data = await res.json();

    let latestPhoto = null;
    let latestVideo = null;

    for (const item of (data.feed || [])) {
      const post = item.post;
      if (!post) continue;

      // Skip reposts
      if (post.reason?.$type === "app.bsky.feed.defs#reasonRepost") continue;

      const embed = post.embed;
      if (!embed) continue;

      // Photo
      if (!latestPhoto && embed.$type === "app.bsky.embed.images#view" && embed.images?.length > 0) {
        const img = embed.images[0];
        latestPhoto = { url: img.fullsize || img.thumb, rkey: post.uri.split("/").pop() };
      }

      // Video — handles a few different embed types
      if (!latestVideo) {
        if ((embed.$type === "app.bsky.embed.video#view" || embed.$type === "app.bsky.embed.video#viewExternal") && embed.playlist) {
          latestVideo = { url: embed.playlist, rkey: post.uri.split("/").pop(), thumb: embed.thumbnail || "" };
        } else if (embed.$type === "app.bsky.embed.recordWithMedia#view" && embed.media) {
          const media = embed.media;
          if (media.playlist) {
            latestVideo = { url: media.playlist, rkey: post.uri.split("/").pop(), thumb: media.thumbnail || "" };
          }
        }
      }

      if (latestPhoto && latestVideo) break;
    }

    // Render photo
    if (latestPhoto && photoEl) {
      photoEl.innerHTML = `
        <a href="https://bsky.app/profile/${handle}/post/${latestPhoto.rkey}" target="_blank" rel="noopener">
          <img src="${latestPhoto.url}" style="max-width:100%;border-radius:12px;">
        </a>`;
    } else if (photoEl) photoEl.textContent = "No recent photo.";

    // Render video
    if (latestVideo && videoEl) {
      videoEl.innerHTML = `
        <a href="https://bsky.app/profile/${handle}/post/${latestVideo.rkey}" target="_blank" rel="noopener">
          <video controls style="max-width:100%;border-radius:12px;" ${latestVideo.thumb ? `poster="${latestVideo.thumb}"` : ""}>
            <source src="${latestVideo.url}">
            Your browser does not support the video tag.
          </video>
        </a>`;
    } else if (videoEl) videoEl.textContent = "No recent video.";

  } catch (err) {
    console.error("Failed to load Bluesky media:", err);
    if (photoEl) photoEl.textContent = "Failed to load photo.";
    if (videoEl) videoEl.textContent = "Failed to load video.";
  }
}

loadBlueskyMedia();
```

---

### **Tools & Skills**

- Bluesky AT Protocol API
- Vanilla JavaScript (async/await, fetch)
- HTML
- Jekyll
- GitHub Pages
- AI-assisted development

---

<div class="image-row">
  <img src="/assets/images/blog/2026-03-21/ss1.png" alt="Bluesky media widget screenshot 1">
  <img src="/assets/images/blog/2026-03-21/ss2.png" alt="Bluesky media widget screenshot 2">
</div>