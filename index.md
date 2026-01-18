---
layout: default
title: Home
---

<section class="hero">
  <div class="container">
    <h1>StockholmFoss 2026</h1>
    <p class="tagline">"Nordic Open Source: Building Sovereign, Sustainable Digital Futures"</p>
    <div class="hero-details">
      <span class="hero-detail">Saturday, May 23rd, 2026</span>
      <span class="hero-detail">KTH Royal Institute of Technology</span>
      <span class="hero-detail">Stockholm, Sweden</span>
    </div>
    <a href="{{ '/schedule/' | relative_url }}" class="hero-cta">View the Schedule</a>
  </div>
</section>

<section class="section">
  <div class="container">
    <div class="quick-facts">
      <div class="fact">
        <div class="fact-number">FREE</div>
        <div class="fact-label">Admission</div>
      </div>
      <div class="fact">
        <div class="fact-number">5</div>
        <div class="fact-label">Tracks</div>
      </div>
      <div class="fact">
        <div class="fact-number">50+</div>
        <div class="fact-label">Speakers</div>
      </div>
      <div class="fact">
        <div class="fact-number">1</div>
        <div class="fact-label">Amazing Day</div>
      </div>
    </div>
  </div>
</section>

<section class="section section-alt">
  <div class="container">
    <h2>Keynote Speakers</h2>
    <div class="keynotes-grid">
      <div class="keynote-card">
        <div class="talk-time">09:00 - Opening Keynote</div>
        <h3>"FOSS in the Age of AI Agents and Digital Sovereignty"</h3>
        <p class="talk-speaker">Olle Jonsson, Maintainer & Open Source Advocate</p>
        <p>As AI coding assistants rewrite our patches and corporations race to dominate AI infrastructure, what does software freedom mean in 2026?</p>
      </div>
      <div class="keynote-card">
        <div class="talk-time">10:00 - Keynote</div>
        <h3>"From Uppsala to the World: 30 Years of MySQL and the Swedish Open Source Legacy"</h3>
        <p class="talk-speaker">Kajsa Lindström, Database Historian & Former MySQL AB Engineer</p>
        <p>Sweden gave the world MySQL, Spotify's open source contributions, and a culture of pragmatic engineering. What can we learn from Nordic FOSS history?</p>
      </div>
      <div class="keynote-card">
        <div class="talk-time">17:00 - Closing Keynote</div>
        <h3>"Funding the Commons: New Models for Open Source Sustainability"</h3>
        <p class="talk-speaker">Erik Andersson, Founder of Polar</p>
        <p>Open source maintainers burn out while billion-dollar companies profit from their work. A frank discussion about what sustainable open source actually requires.</p>
      </div>
    </div>
  </div>
</section>

<section class="section">
  <div class="container">
    <h2>Five Tracks, One Day</h2>
    <p class="section-intro">Choose your own adventure through the world of Nordic open source, from infrastructure to community building.</p>
    <div class="info-grid">
      <div class="info-card">
        <h3>Main Track</h3>
        <p>Aula Magna - Keynotes and major topics including supply chain security, digital sovereignty, and the state of the Linux desktop.</p>
      </div>
      <div class="info-card">
        <h3>Infrastructure</h3>
        <p>Sal A - Kubernetes at scale, PostgreSQL tuning, NixOS in production, and running your own email in 2026.</p>
      </div>
      <div class="info-card">
        <h3>Development</h3>
        <p>Sal B - Rust in embedded systems, Python type hints, WebAssembly, CRDTs, and the modern terminal workflow.</p>
      </div>
      <div class="info-card">
        <h3>Community & Governance</h3>
        <p>Sal C - Maintainer survival, EU Cyber Resilience Act, inclusive communities, and teaching open source.</p>
      </div>
      <div class="info-card">
        <h3>Nordic Focus</h3>
        <p>Sal D - Swedish language AI, Nordic digital identity, open source in defense, and preserving Sami languages.</p>
      </div>
      <div class="info-card">
        <h3>Lightning Talks</h3>
        <p>Aula Magna (16:00) - Ten rapid-fire talks from Swedish keyboard firmware to Blåhaj-as-a-Service.</p>
      </div>
    </div>
    <p class="text-center mt-2">
      <a href="{{ '/schedule/' | relative_url }}" class="hero-cta">Full Schedule</a>
    </p>
  </div>
</section>

<section class="section section-alt">
  <div class="container">
    <h2>Featured Speakers</h2>
    <div class="speakers-grid">
      {% assign featured_speakers = site.speakers | where_exp: "s", "s.keynote == true" | slice: 0, 6 %}
      {% if featured_speakers.size == 0 %}
        {% assign featured_speakers = site.speakers | slice: 0, 6 %}
      {% endif %}
      {% for speaker in featured_speakers %}
      <a href="{{ speaker.url | relative_url }}" class="speaker-card">
        <div class="speaker-avatar">{{ speaker.name | split: ' ' | map: 'first' | join: '' | upcase | truncate: 2, '' }}</div>
        <h3>{{ speaker.name }}</h3>
        <p class="speaker-title">{{ speaker.title }}</p>
        {% if speaker.track %}
        <span class="track-badge track-{{ speaker.track | slugify }}">{{ speaker.track }}</span>
        {% endif %}
      </a>
      {% endfor %}
    </div>
    <p class="text-center mt-2">
      <a href="{{ '/speakers/' | relative_url }}" class="hero-cta">All Speakers</a>
    </p>
  </div>
</section>

<section class="section">
  <div class="container">
    <h2>Practical Information</h2>
    <div class="info-grid">
      <div class="info-card">
        <h3>Location</h3>
        <p><strong>KTH Royal Institute of Technology</strong><br>
        Brinellvägen 8, 114 28 Stockholm</p>
        <p>Nearest T-bana: Tekniska högskolan (Red line)</p>
      </div>
      <div class="info-card">
        <h3>Fika</h3>
        <p>Coffee, tea, and kanelbullar provided during breaks.</p>
        <p><em>Sponsored by Redpill Linpro and Open Source Sweden</em></p>
      </div>
      <div class="info-card">
        <h3>After-Party</h3>
        <p><strong>18:00 onwards</strong> at Nymble Student Union</p>
        <p>First drink free, sponsored by Polar and Mullvad VPN</p>
      </div>
    </div>
    <p class="text-center mt-2">
      <a href="{{ '/practical/' | relative_url }}" class="hero-cta">More Info</a>
    </p>
  </div>
</section>
