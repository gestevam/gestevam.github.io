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
    <div class="row" style="padding-top: 60px; margin-top: -60px;" id="{{ publication.pmid }}">
      <div>
        <h5 class="publication-title">{{ publication.title | markdownify | remove: '<p>' | remove: '</p>' }}</h5>
        <h6 class="publication-authors">{{ publication.authors | markdownify | remove: '<p>' | remove: '</p>' }}</h6>

        {% if publication.journal %}
          <i>{{ publication.journal }},</i>
        {% else %}
          <i>Preprint,</i>
        {% endif %}

        {{ publication.pub_date | split: "-" | first }}
      </div>
    </div>

    <!-- flexbox-->
    <div class="row publication-content">
      <!-- key fig, left -->
      <div class="col-sm-6 publication-image">
        <img class="img-fluid" src="{{ publication.image }}" alt="Key Figure" style="max-height: 200px;">
      </div>

      <!-- links, right -->
      <div class="col-sm-6 publication-links-container">
        <h6>Access the Paper</h6>
        <ul class="publication-links">
          {% if publication.pmid %}
            <li>PMID: <a href="http://www.ncbi.nlm.nih.gov/pubmed/{{ publication.pmid }}" target="_blank">{{ publication.pmid }}</a></li>
          {% endif %}
          {% if publication.pdf %}
            <li><a href="{{ publication.pdf }}" target="_blank">Full Text</a></li>
          {% endif %}
          {% if publication.biorxiv_version %}
            <li><a href="https://doi.org/{{ publication.biorxiv_version }}" target="_blank">Biorxiv Version</a></li>
          {% endif %}
        </ul>

        <h6>Additional Links</h6>
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

    <hr>

  {% endfor %}
</div>
