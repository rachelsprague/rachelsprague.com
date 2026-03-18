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
  <div class="section-card">
    <p>
      I focus on building clear, usable data systems. Outside of work, I build and maintain personal web projects as a way to experiment with design, data, and small technical ideas. This site is part of that ongoing process.
    </p>
  </div>

  <!-- Currently -->
  <div class="section-card">
    <span class="title">Currently</span>
    <p id="currently-text">Experimenting with Jekyll layouts, refining UI details, and iterating on small web projects.</p>
  </div>

  <!-- Selected Work -->
  <div class="section-card">
    <span class="title">Selected Work</span>
    <ul>
      <li>Custom Jekyll sites (3+ personal projects)</li>
      <li>Last.fm, Twitch, Bluesky widgets</li>
      <li>GitHub Pages experimentation & layout exploration</li>
    </ul>
  </div>

  <!-- Links & Resources -->
  <div class="section-card">
    <h2>Links & Resources</h2>

    <div class="subsection">
      <h3>Links</h3>
      <a href="/about">About Me</a>
    </div>

    <div class="subsection">
      <h3>Resources</h3>
      <a href="https://datasetsearch.research.google.com/" target="_blank">Google Dataset Search</a>
      <a href="https://www.kaggle.com/datasets" target="_blank">Kaggle Datasets</a>
    </div>
  </div>

  <!-- Optional Buttons -->
  <a class="btn btn--primary btn--large btn--block" href="https://www.raych.com" target="_blank" rel="noopener">Raych</a>
  <a class="btn btn--primary btn--large btn--block" href="http://www.raych.com/makes/" target="_blank" rel="noopener">Raych Makes</a>

</div>

<!-- Rotating Currently Lines Script -->
<script>
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
    const line = currentlyLines[Math.floor(Math.random() * currentlyLines.length)];
    currentlyText.textContent = line;
  }
</script>