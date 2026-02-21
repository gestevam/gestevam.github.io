---
layout: default
title: publications
permalink: /publications/
body_class: publications-page
---

<h1 class="publications-title">Publications</h1>
<hr class="publications-line">

<div class="container-fluid">
  {% assign sorted = site.publications | sort: "pub_date" | reverse %}
  {% for publication in sorted %}

    <div class="pub-entry" style="padding-top: 60px; margin-top: -60px;" id="{{ publication.pmid }}">

      <!-- Key figure, centered and wide -->
      {% if publication.image %}
      <div class="pub-figure">
        <img src="{{ publication.image }}" alt="Key Figure">
      </div>
      {% endif %}

      <!-- Title, journal, year, authors -->
      <div class="pub-header">
        <h4 class="publication-title">{{ publication.title | markdownify | remove: '<p>' | remove: '</p>' }}</h4>

        {% if publication.journal %}
          <p><em>{{ publication.journal }}</em><br>
        {% else %}
          <p><em>Preprint</em><br>
        {% endif %}
        {{ publication.pub_date | split: "-" | first }}</p>

        <p class="publication-authors">{{ publication.authors | markdownify | remove: '<p>' | remove: '</p>' }}</p>
      </div>

      <!-- Abstract -->
      {% if publication.abstract %}
      <div class="pub-abstract">
        {{ publication.abstract }}
      </div>
      {% endif %}

      <!-- Links -->
      <div class="pub-links">
        <div class="pub-col">
          <strong>Access the Paper</strong>
          <ul class="publication-links">
            {% if publication.pmid %}
              <li>PMID: <a href="http://www.ncbi.nlm.nih.gov/pubmed/{{ publication.pmid }}" target="_blank">{{ publication.pmid }}</a></li>
            {% endif %}
            {% if publication.pdf %}
              <li><a href="{{ publication.pdf }}" target="_blank">Full Text</a></li>
            {% endif %}
            {% if publication.biorxiv_version %}
              <li><a href="https://doi.org/{{ publication.biorxiv_version }}" target="_blank">Biorxiv Preprint</a></li>
            {% endif %}
          </ul>
        </div>

        <div class="pub-col">
          <strong>Additional Links</strong>
          <ul class="publication-links">
            {% if publication.github %}
              <li>
                <a href="https://github.com/{{ publication.github[0].url }}" target="_blank">{{ publication.github[0].description }}</a>
              </li>
            {% endif %}
            {% for link in publication.links %}
              <li><a href="{{ link.url }}" target="_blank">{{ link.name }}</a></li>
            {% endfor %}
          </ul>
        </div>
      </div>

    </div>

    <hr>

  {% endfor %}
</div>
