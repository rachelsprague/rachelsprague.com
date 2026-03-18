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
  <div class="landing-bio">
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
  <div class="landing-bio">
    <p>
      I focus on building clear, usable data systems. Outside of work, I build and maintain personal web projects as a way to experiment with design, data, and small technical ideas. This site is part of that ongoing process.
    </p>
  </div>

  <!-- Main Links -->
  <h2>Links</h2>
  <a href="/about">About Me</a>

  <!-- Currently rotating widget -->
  <div class="landing-bio">
    <span class="title">Currently</span>
    <p id="currently-text">
      <!-- Placeholder, populated by JS -->
    </p>
  </div>

  <!-- Selected Work -->
  <div class="landing-bio">
    <span class="title">Selected Work</span>
    <p>
      A few small web experiments and utilities I've built. Screenshots and links coming soon:
    </p>
    <ul>
      <li>Personal Jekyll pages & small UI experiments</li>
      <li>Custom Last.fm / Spotify widgets</li>
      <li>Data exploration and visualization demos</li>
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

  const currentlyText = document.getElementById("currently-text");
  if (currentlyText) {
    // Pick a random line on each page load
    const line = currentlyLines[Math.floor(Math.random() * currentlyLines.length)];
    currentlyText.textContent = line;
  }
</script>