---
layout: default
title: Speakers
permalink: /speakers/
---

<header class="page-header">
  <div class="container">
    <h1>Speakers</h1>
    <p class="subtitle">50+ speakers sharing their expertise in open source</p>
  </div>
</header>

<div class="page-content">
  <div class="container">

<div class="schedule-tabs" role="tablist">
  <button class="schedule-tab active" onclick="filterSpeakers('all')" role="tab">All Speakers</button>
  <button class="schedule-tab" onclick="filterSpeakers('keynote')" role="tab">Keynotes</button>
  <button class="schedule-tab" onclick="filterSpeakers('main')" role="tab">Main</button>
  <button class="schedule-tab" onclick="filterSpeakers('infrastructure')" role="tab">Infrastructure</button>
  <button class="schedule-tab" onclick="filterSpeakers('development')" role="tab">Development</button>
  <button class="schedule-tab" onclick="filterSpeakers('community')" role="tab">Community</button>
  <button class="schedule-tab" onclick="filterSpeakers('nordic-focus')" role="tab">Nordic</button>
  <button class="schedule-tab" onclick="filterSpeakers('lightning')" role="tab">Lightning</button>
</div>

<section class="section">
  <h2>Keynote Speakers</h2>
  <div class="speakers-grid" data-track="keynote">
    {% assign keynote_speakers = site.speakers | where: "keynote", true %}
    {% for speaker in keynote_speakers %}
    <a href="{{ speaker.url | relative_url }}" class="speaker-card" data-track="{{ speaker.track | slugify }}">
      <div class="speaker-avatar">{{ speaker.name | split: ' ' | map: 'first' | join: '' | upcase | truncate: 2, '' }}</div>
      <h3>{{ speaker.name }}</h3>
      <p class="speaker-title">{{ speaker.title | truncate: 80 }}</p>
      {% if speaker.track %}
      <span class="track-badge track-{{ speaker.track | slugify }}">{{ speaker.track }}</span>
      {% endif %}
    </a>
    {% endfor %}
  </div>
</section>

<section class="section section-alt">
  <h2>All Speakers</h2>
  <div class="speakers-grid" id="speakers-grid">
    {% assign sorted_speakers = site.speakers | where_exp: "s", "s.keynote != true" | sort: "name" %}
    {% for speaker in sorted_speakers %}
    {% unless speaker.track == "Organizer" %}
    <a href="{{ speaker.url | relative_url }}" class="speaker-card" data-track="{{ speaker.track | slugify }}">
      <div class="speaker-avatar">{{ speaker.name | split: ' ' | map: 'first' | join: '' | upcase | truncate: 2, '' }}</div>
      <h3>{{ speaker.name }}</h3>
      <p class="speaker-title">{{ speaker.title | truncate: 80 }}</p>
      {% if speaker.track %}
      <span class="track-badge track-{{ speaker.track | slugify }}">{{ speaker.track }}</span>
      {% endif %}
    </a>
    {% endunless %}
    {% endfor %}
  </div>
</section>

<section class="section">
  <h2>Organizing Committee</h2>
  <div class="speakers-grid">
    {% assign organizers = site.speakers | where: "track", "Organizer" %}
    {% for speaker in organizers %}
    <a href="{{ speaker.url | relative_url }}" class="speaker-card" data-track="organizer">
      <div class="speaker-avatar">{{ speaker.name | split: ' ' | map: 'first' | join: '' | upcase | truncate: 2, '' }}</div>
      <h3>{{ speaker.name }}</h3>
      <p class="speaker-title">{{ speaker.title | truncate: 80 }}</p>
    </a>
    {% endfor %}
  </div>
</section>

<script>
function filterSpeakers(track) {
  // Update tab styles
  document.querySelectorAll('.schedule-tab').forEach(tab => tab.classList.remove('active'));
  event.target.classList.add('active');

  // Filter cards
  document.querySelectorAll('.speaker-card').forEach(card => {
    if (track === 'all' || card.dataset.track === track) {
      card.style.display = '';
    } else {
      card.style.display = 'none';
    }
  });
}
</script>

  </div>
</div>
