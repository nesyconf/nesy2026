---
layout: page
title: Keynote Speakers
permalink: /speakers/
---

<style>
/* ===== Layout ===== */

.speakers-section {
  margin: 3rem 0 3.5rem;
}

.speakers-title {
  font-size: 1.6rem;
  font-weight: 700;
  margin: 0 0 1.2rem;
}

.small-muted {
  color: rgba(0,0,0,.65);
  font-size: 1.05rem;
}

/* Always stacked, full width */
.speakers-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.6rem;
}

/* ===== Speaker card ===== */

.speaker-card {
  position: relative;
  display: grid;
  grid-template-columns: 112px 1fr;
  gap: 1.25rem;
  padding: 1.4rem;
  border: 1.5px solid rgba(0,0,0,.15);
  border-radius: 12px;
  background: #fff;
}

.speaker-photo {
  width: 112px;
  height: 112px;
  border-radius: 8px;
  object-fit: cover;
  background: rgba(0,0,0,.04);
}

.speaker-name {
  font-weight: 700;
  font-size: 1.15rem;
  margin: 0;
  line-height: 1.25;
}

.speaker-meta {
  margin: .35rem 0 0;
  font-size: 1.05rem;
  color: rgba(0,0,0,.75);
}

.speaker-bio {
  margin: .7rem 0 0;
  font-size: 1rem;
  line-height: 1.55;
  color: rgba(0,0,0,.85);
}

/* Hover polish */
@media (hover: hover) {
  .speaker-card:hover {
    box-shadow: 0 6px 18px rgba(0,0,0,.08);
  }
}

/* Mobile refinement */
@media (max-width: 480px) {
  .speaker-card {
    grid-template-columns: 1fr;
  }
  .speaker-photo {
    width: 100%;
    height: auto;
    aspect-ratio: 1 / 1;
  }
}
</style>

{% assign speakers = site.speakers | sort: "name" %}

<div class="speakers-section">

  {% if speakers.size > 0 %}
    <div class="speakers-grid">
      {% for p in speakers %}
        <div class="speaker-card">
          <img class="speaker-photo"
               src="{{ p.photo | default: '/assets/img/speakers/placeholder.png' }}"
               alt="{{ p.name | default: p.title }}">
          <div>
            <p class="speaker-name">
              {% if p.url %}
                <a href="{{ p.url }}">{{ p.name | default: p.title }}</a>
              {% else %}
                {{ p.name | default: p.title }}
              {% endif %}
            </p>

            {% if p.institution %}
              <p class="speaker-meta">{{ p.institution }}</p>
            {% endif %}

            {% if p.talk_title %}
              <p class="speaker-meta"><strong>Talk:</strong> {{ p.talk_title }}</p>
            {% endif %}

            {% if p.excerpt %}
              <div class="speaker-bio">{{ p.excerpt }}</div>
            {% elsif p.content != "" %}
              <div class="speaker-bio">{{ p.content }}</div>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% else %}
    <p class="small-muted">Speakers will be announced soon.</p>
  {% endif %}
</div>

<p style="margin-top:2rem; font-size:1.1rem; font-weight:600;">
</p>
