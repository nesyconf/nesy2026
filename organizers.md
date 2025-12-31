---
layout: page
title: Organizers
permalink: /organizers/
---

<style>
/* ===== Layout ===== */

.role-section {
  margin: 3rem 0 3.5rem;
}

.role-title {
  font-size: 1.6rem;
  font-weight: 700;
  margin: 0 0 1.2rem;
}

.small-muted {
  color: rgba(0,0,0,.65);
  font-size: 1.05rem;
}

/* Always stacked, full width */
.people-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.6rem;
}

/* ===== Person card ===== */

.person-card {
  position: relative;
  display: grid;
  grid-template-columns: 112px 1fr;
  gap: 1.25rem;
  padding: 1.4rem;
  border: 1.5px solid rgba(0,0,0,.15);
  border-radius: 12px;
  background: #fff;
}

.person-photo {
  width: 112px;
  height: 112px;
  border-radius: 8px;
  object-fit: cover;
  background: rgba(0,0,0,.04);
}

.person-name {
  font-weight: 700;
  font-size: 1.15rem;
  margin: 0;
  line-height: 1.25;
}

.person-meta {
  margin: .35rem 0 0;
  font-size: 1.05rem;
  color: rgba(0,0,0,.75);
}

.person-email {
  margin: .45rem 0 0;
  font-size: 1.05rem;
}

.person-email a {
  text-decoration: none;
}

.person-email a:hover {
  text-decoration: underline;
}

/* Hover polish */
@media (hover: hover) {
  .person-card:hover {
    box-shadow: 0 6px 18px rgba(0,0,0,.08);
  }
}

/* Mobile refinement */
@media (max-width: 480px) {
  .person-card {
    grid-template-columns: 1fr;
  }
  .person-photo {
    width: 100%;
    height: auto;
    aspect-ratio: 1 / 1;
  }
}
</style>

{% assign committee = site.data.organizers.organisation_committee %}
{% assign roles = committee | map: "role" | uniq %}

<!-- ================= Organisation Committee ================= -->

<div class="role-section">
  <h2 class="role-title">NeSy 2026 Organisation Committee</h2>

  {% for r in roles %}
    <h3 class="small-muted" style="margin: 1.6rem 0 .9rem;">{{ r }}</h3>

    <div class="people-grid">
      {% for p in committee %}
        {% if p.role == r %}
          <div class="person-card">
            <img class="person-photo"
                 src="{{ p.photo | default: '/assets/img/organizers/placeholder.png' }}"
                 alt="{{ p.name }}">
            <div>
              <p class="person-name">
                {% if p.url %}<a href="{{ p.url }}">{{ p.name }}</a>{% else %}{{ p.name }}{% endif %}
              </p>
              {% if p.institution %}<p class="person-meta">{{ p.institution }}</p>{% endif %}
              {% if p.email %}<p class="person-email"><a href="mailto:{{ p.email }}">{{ p.email }}</a></p>{% endif %}
            </div>
          </div>
        {% endif %}
      {% endfor %}
    </div>
  {% endfor %}
</div>

<!-- ================= Volunteer Team (single list) ================= -->

{% if site.data.organizers.volunteer_team %}
<div class="role-section">
  <h2 class="role-title">NeSy 2026 Volunteer Team</h2>

  {% assign volunteers = site.data.organizers.volunteer_team | sort: "name" %}

  <div class="people-grid">
    {% for p in volunteers %}
      <div class="person-card">
        <img class="person-photo"
             src="{{ p.photo | default: '/assets/img/organizers/placeholder.png' }}"
             alt="{{ p.name }}">
        <div>
          <p class="person-name">
            {% if p.url %}<a href="{{ p.url }}">{{ p.name }}</a>{% else %}{{ p.name }}{% endif %}
          </p>
          {% if p.institution %}
            <p class="person-meta">{{ p.institution }}</p>
          {% endif %}
          {% if p.email %}
            <p class="person-email">
              <a href="mailto:{{ p.email }}">{{ p.email }}</a>
            </p>
          {% endif %}
        </div>
      </div>
    {% endfor %}
  </div>
</div>
{% endif %}
