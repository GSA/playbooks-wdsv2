---
layout: page
collection: fpki
title: Announcements
permalink: fpki/announcements/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: Active
    href: ../announcements/test-tools/
  - text: Archived
    href: ../announcements/2019fpkimigration/
---

{% assign categories = "" | split: "" %}
{% for guide in site.fpkiannouncements %}
  {% assign categoryName = guide.category | strip %}
  {% assign categories = categories | push: categoryName | uniq | sort %}
{% endfor %}
{% assign categories = categories | uniq | sort %}

These announcements and hot topic concern Federal Public Key Infrastructure changes that may affect your agency's operations. Announcements are archived after one year and removed after three years.

<div class="usa-width-one-fourth">
  <fieldset class="usa-fieldset-inputs guides-filter">
    <legend>Status</legend>
    <ul class="usa-unstyled-list">
      {% for category in categories %}
      <li>
        <input class="guides-filter-category" id="category-{{ category | slugify }}" type="checkbox" name="categories" value="{{ category }}" checked>
        <label for="category-{{ category | slugify }}">{{ category }}</label>
      </li>
      {% endfor %}
    </ul>
  </fieldset>
</div>

<table class="usa-table--borderless announce-table">
  <thead class="usa-sr-only">
    <tr>
      <th id="announce-table-heading-title" scope="col">Title</th>
      <th id="announce-table-heading-status" scope="col">Status</th>
      <th id="announce-table-heading-date" scope="col">Date</th>
      <th id="announce-table-heading-description" scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    {% for category in categories %}
        <tr class="guides-table-category-heading" data-category="{{ category }}">
          <th colspan="4" class="guides-table-heading" id="guides-table-heading-{{ category | slugify }}"><b>{{ category }} Status</b></th>
        </tr>
        {% for guide in site.fpkiannouncements %}
          {% if guide.category == category %}
        <tr class="announce-table-row">
          <td><a href="{{ announcement.url | relative_url }}">{{ announcement.title }}</a></td>
          <td>{{ announcement.status }}</td>
          <td>{{ announcement.pubDate }}</td>
          <td>{{ announcement.description }}</td>
        </tr>
      {% endif %}
     {% endfor %}
    {% endfor %}
  </tbody>
</table>
