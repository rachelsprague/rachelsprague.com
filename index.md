---
layout: default
title: Rachel Sprague
---

<div class="landing-container">

  <!-- Logo / Icon -->
  <img src="/assets/images/logo.png" alt="Rachel Sprague" class="logo">

  <!-- Social media icons inline -->
  <div class="social-icons-inline">
    <a href="https://github.com/rachelsprague" target="_blank">
      <img src="/assets/images/github.svg" alt="GitHub" />
    </a>
    <a href="https://www.linkedin.com/in/rachelsprague/" target="_blank">
      <img src="/assets/images/linkedin.svg" alt="LinkedIn" />
    </a>
  </div>

  <!-- Title + Skills -->
  <div class="landing-bio section-card">
    <span class="title">Senior Data Analyst</span> <br/>
    
    <span class="skill">SQL</span>
    <span class="dot-separator">•</span>
    <span class="skill">dbt</span>
    <span class="dot-separator">•</span>
    <span class="skill">Snowflake</span>
    <span class="dot-separator">•</span>
    <span class="skill">Analytics Engineering</span>
  </div>

  <!-- About snippet -->
  <div class="landing-bio section-card">
    <p>
      I focus on building clear, usable data systems. Outside of work, I build and maintain personal web projects as a way to experiment with design, data, and small technical ideas. This site is part of that ongoing process.
    </p>
  </div>

  <!-- Main Links -->
  <h2>Links</h2>
  <a href="/about">About Me</a>

  <!-- Currently Section -->
  <div class="landing-bio section-card">
    <span class="title">Currently</span>
    <ul id="currently-text"></ul>
  </div>

  <!-- Selected Work -->
  <div class="landing-bio section-card">
    <span class="title">Selected Work</span>
    <ul>
      <li>Creating custom widgets for Last.fm, Twitch, and Bluesky</li>
      <li>Building three small Jekyll/GitHub Pages sites in a Linktree style</li>
      <li>Experimenting with interactive layouts and CSS tricks</li>
      <li>Future project: personal analytics dashboard using music APIs</li>
    </ul>
  </div>

  <!-- Resources Section -->
  <h2>Resources</h2>
  <a href="https://datasetsearch.research.google.com/" target="_blank">Google Dataset Search</a>
  <a href="https://www.kaggle.com/datasets" target="_blank">Kaggle Datasets</a>

</div>

<script>
  // Rotating "Currently" lines
  const currentlyLines = [
    "Claude.",
    "Prompting.",
    "Adding one more widget.",
    "Whack-a-CSS-issue.",
    "Fixing 1 layout issue, creating two more.",
    "Exploring Github Pages in 2026.",
    "Trying to convince myself I enjoy debugging CSS."
  ];

  const currentlyEl = document.getElementById("currently-text");
  if (currentlyEl) {
    const count = 3; // number of lines to show
    const shuffled = currentlyLines.sort(() => 0.5 - Math.random());
    const selected = shuffled.slice(0, count);
    currentlyEl.innerHTML = selected.map(line => `<li>${line}</li>`).join("");
  }
</script>