---
layout: page
title: Organizers
permalink: /organizers/
---

<style>
/* Committee-like layout */
.role-section { margin: 2.2rem 0 2.8rem; }
.role-title { font-size: 1.4rem; font-weight: 700; margin: 0 0 1rem; }
.people-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 1.25rem;
}
.person-card {
  display: grid;
  grid-template-columns: 96px 1fr;
  gap: 1rem;
  padding: 1rem;
  border: 1px solid rgba(0,0,0,.12);
  border-radius: 10px;
  background: #fff;
}
.person-photo {
  width: 96px; height: 96px;
  border-radius: 6px;
  object-fit: cover;
  background: rgba(0,0,0,.04);
}
.person-name { font-weight: 700; margin: 0; line-height: 1.2; }
.person-meta { margin: .25rem 0 0; color: rgba(0,0,0,.75); }
.person-email { margin: .35rem 0 0; }
.person-email a { text-decoration: none; }
.person-email a:hover { text-decoration: underline; }
.small-muted { color: rgba(0,0,0,.65); font-size: .95rem; }
</style>

{% assign committee = site.data.organizers.organisation_committee %}
{% assign roles = committee | map: "role" | uniq %}

<div class="role-section">
  <h2 class="role-title">NeSy 2026 Organisation Committee</h2>

  {% for r in roles %}
    <h3 class="small-muted" style="margin: 1.4rem 0 .8rem;">{{ r }}</h3>

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


{% if site.data.organizers.executive_board %}
<div class="role-section">
  <h2 class="role-title">NeSy Executive Board</h2>
  <div class="people-grid">
    {% for p in site.data.organizers.executive_board %}
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
    {% endfor %}
  </div>
</div>
{% endif %}


{% if site.data.organizers.advisory_board %}
<div class="role-section">
  <h2 class="role-title">NeSy Advisory Board</h2>
  <div class="people-grid">
    {% for p in site.data.organizers.advisory_board %}
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
    {% endfor %}
  </div>
</div>
{% endif %}
