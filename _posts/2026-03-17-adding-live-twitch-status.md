---
layout: page
title: "Adding Live Twitch Status to a Static Site (Without a Backend)"
date: 2026-03-17
body_class: blog-post
subtitle: "How I show live Twitch status on a static Jekyll site without a backend"
---

Adding a live Twitch status indicator to a static site can be tricky if you don’t want to set up a backend. Here’s how I did it using just a simple API and a bit of JavaScript.

## The Goal

I wanted a card on my site that:

- Shows whether my stream is live
- Displays the duration if live
- Updates automatically every minute
- Works on a static Jekyll site without a backend

## Step 1: HTML Structure

I created a simple card in my `index.md`:

    <div id="twitch-status" class="twitch-card">
      <a href="https://www.twitch.tv/raych_com" target="_blank" rel="noopener">
        <div class="text-block">
          <strong id="twitch-text">🐠 Stream Offline</strong>
          <span class="duration"></span>
        </div>
      </a>
    </div>

## Step 2: JavaScript to Fetch Status

I use [decapi.me](https://decapi.me) for a simple Twitch uptime API. Here's the JS:

    async function updateTwitchStatus() {
      try {
        const res = await fetch("https://decapi.me/twitch/uptime/raych_com");
        const text = await res.text();

        const card = document.getElementById("twitch-status");
        const textBlock = card.querySelector(".text-block");
        const mainText = textBlock.querySelector("#currently-text");
        const durationEl = textBlock.querySelector(".duration");

        // Simple fade animation
        card.style.opacity = 0;
        card.style.transform = "translateY(4px)";

        setTimeout(() => {
          if (text.toLowerCase().includes("offline")) {
            mainText.textContent = `🐠 Aquarium stream offline`;
            durationEl.textContent = "";
            card.classList.remove("live");
          } else {
            mainText.textContent = `🐠 Live on Twitch`;
            durationEl.textContent = text;
            card.classList.add("live");
          }

          card.style.opacity = 1;
          card.style.transform = "translateY(0)";
        }, 300);

      } catch (err) {
        console.error("Failed to fetch Twitch status:", err);
        const card = document.getElementById("twitch-status");
        const textBlock = card.querySelector(".text-block");
        textBlock.querySelector("#currently-text").textContent = "🐠 Stream status unavailable";
        textBlock.querySelector(".duration").textContent = "";
      }
    }

    // Initial load + refresh every 60s
    updateTwitchStatus();
    setInterval(updateTwitchStatus, 60000);

## Step 3: Styling

I added a card style in `style.css`:

    .twitch-card {
      background: rgba(0,0,0,0.2);
      padding: 1rem 1.5rem;
      border-radius: 12px;
      margin: 1rem auto;
      max-width: 320px;
      color: #fff;
      transition: background 0.3s ease;
      text-align: center;
    }

    .twitch-card.live {
      background: rgba(0, 128, 255, 0.3);
    }

## Step 4: Result

- The card updates automatically every 60 seconds.
- Shows “Live” or “Offline” instantly.
- Works on a completely static Jekyll site, no backend required.

![Screenshot of Twitch Status Card](path/to/screenshot.png)

## Optional Personal Touch

I sprinkled in a rotating “Currently” line for fun. Things like:

- “Whack-a-CSS-issue”
- “Trying to convince myself I enjoy debugging CSS”

Because what’s a static site without a little humor?

## Next Steps / Ideas

- Add a hover tooltip with the stream title
- Integrate other APIs (like YouTube or Bluesky) in a similar way
- Animate the status card for subtle feedback when the stream goes live

<p><a href="/">← Back to Home</a></p>