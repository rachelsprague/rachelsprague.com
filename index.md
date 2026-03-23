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
    <a href="https://www.linkedin.com/in/rsprague/" target="_blank">
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
    <span class="dot-separator">•</span>
    <span class="skill">AI-assisted coding</span>
  </div>

  <!-- About snippet -->
  <div class="section-card">
    <p>
      Senior Data Analyst focused on building clear, usable data systems. Outside of work, I build and maintain personal web projects — this site is one of them.
    </p>
  </div>

  <!-- Currently -->
  <div class="section-card">
    <span class="title">Currently:</span>
    <p id="currently-text">Experimenting with Jekyll layouts, refining UI details, and iterating on small web projects.</p>
  </div>

  <!-- Selected Work -->
  <div class="section-card">
    <span class="title">Projects:</span>
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
      <a href="/about">About</a>
      <a href="/blog">Blog</a>
    </div>

    <div class="subsection">
      <h3>Resources</h3>
      <a href="https://datasetsearch.research.google.com/" target="_blank">Google Dataset Search</a>
      <a href="https://www.kaggle.com/datasets" target="_blank">Kaggle Datasets</a>
    </div>
  </div>

</div>

<!-- Rotating Currently Lines Script -->
<script>
  const currentlyLines = [
    "Claude.",
    "Prompting.",
    "Adding one more widget.",
    "Whack-a-CSS-issue.",
    "Fixing 1 layout issue, creating two more.",
    "Exploring Github Pages.",
    "Trying to convince myself I enjoy debugging CSS."
  ];

  const currentlyText = document.getElementById("currently-text");
  if (currentlyText) {
    const line = currentlyLines[Math.floor(Math.random() * currentlyLines.length)];
    currentlyText.textContent = line;
  }
</script>