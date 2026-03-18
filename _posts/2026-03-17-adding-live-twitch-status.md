---
layout: page
title: "Adding a Live Twitch Status to a Static Site"
date: 2026-03-17
body_class: blog-post
subtitle: "Displaying live Twitch status directly on a Jekyll site"
---

Normally, fetching live data requires a server, but we can pull the Twitch status for a channel directly from the browser using JavaScript. I also added a subtle pulsing animation when live to make it stand out visually.

<p><strong>Live Demo</strong></p>

<div id="twitch-status" class="twitch-card">
  <a href="https://www.twitch.tv/github" target="_blank" rel="noopener">
    <div class="text-block">
      <strong id="twitch-text">🐠 Checking status...</strong>
      <span class="duration"></span>
    </div>
  </a>
</div>

## The Goal

I wanted a card on my site that:

- Shows whether my stream is live
- Displays the duration if live
- Updates automatically every minute
- Works on a completely static Jekyll site

## Step 1: HTML Structure

I added a simple card in my `index.md` (or you can embed it here in the post for a live demo):

    <div id="twitch-status" class="twitch-card">
      <a href="https://www.twitch.tv/github" target="_blank" rel="noopener">
        <div class="text-block">
          <strong id="twitch-text">Stream Offline</strong>
          <span class="duration"></span>
        </div>
      </a>
    </div>

## Step 2: JavaScript to Fetch Status

I use [decapi.me](https://decapi.me) to fetch Twitch uptime. Here’s the JavaScript:

    async function updateTwitchStatus() {
      try {
        const res = await fetch("https://decapi.me/twitch/uptime/github");
        const text = await res.text();

        const card = document.getElementById("twitch-status");
        const textBlock = card.querySelector(".text-block");
        const mainText = textBlock.querySelector("#twitch-text");
        const durationEl = textBlock.querySelector(".duration");

        // Fade animation for smooth update
        card.style.opacity = 0;
        card.style.transform = "translateY(4px)";

        setTimeout(() => {
          if (text.toLowerCase().includes("offline")) {
            mainText.textContent = "🐠 Stream Offline";
            durationEl.textContent = "";
            card.classList.remove("live");
          } else {
            mainText.textContent = "🐠 Live on Twitch";
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
        textBlock.querySelector("#twitch-text").textContent = "🐠 Status unavailable";
        textBlock.querySelector(".duration").textContent = "";
      }
    }

    // Initial load + refresh every 60s
    updateTwitchStatus();
    setInterval(updateTwitchStatus, 60000);

Make sure the ID in your HTML (`#twitch-text`) matches the JavaScript selector.

## Step 3: Styling

Here’s the CSS I added to `style.css`:

    .twitch-card {
      background: rgba(0,0,0,0.2);
      padding: 1rem 1.5rem;
      border-radius: 12px;
      margin: 1rem auto;
      max-width: 320px;
      color: #fff;
      text-align: center;
      transition: background 0.3s ease;
    }

    .twitch-card.live {
      background: rgba(0, 128, 255, 0.3);
    }

    /* Twitch live pulse */
    #twitch-status.live {
      animation: twitchPulse 1.8s infinite ease-in-out;
      border-color: rgba(78, 228, 78, 0.6);
    }

    @keyframes twitchPulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.04); opacity: 0.8; }
    }

The `live` class triggers both the background color and the pulsing animation when the stream is live.

## Step 4: Result

- The card updates automatically every 60 seconds.
- Shows **Live** or **Offline** instantly.
- Pulses subtly when live for attention.
- Works entirely on a static Jekyll site.

![Screenshot of Twitch Status Card](path/to/screenshot.png)

<p><a href="/">← Back to Home</a></p>

<script>
async function updateTwitchStatusPost() {
  try {
    const res = await fetch("https://decapi.me/twitch/uptime/github");
    const text = await res.text();

    const card = document.getElementById("twitch-status");
    if (!card) return;

    const textBlock = card.querySelector(".text-block");
    const mainText = textBlock.querySelector("#twitch-text");
    const durationEl = textBlock.querySelector(".duration");

    if (text.toLowerCase().includes("offline")) {
      mainText.textContent = "🐠 Stream Offline";
      durationEl.textContent = "";
      card.classList.remove("live");
    } else {
      mainText.textContent = "🐠 Live on Twitch";
      durationEl.textContent = text;
      card.classList.add("live");
    }

  } catch {
    const card = document.getElementById("twitch-status");
    if (!card) return;

    const textBlock = card.querySelector(".text-block");
    textBlock.querySelector("#twitch-text").textContent = "🐠 Status unavailable";
    textBlock.querySelector(".duration").textContent = "";
  }
}

updateTwitchStatusPost();
setInterval(updateTwitchStatusPost, 60000);
</script>