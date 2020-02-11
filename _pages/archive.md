---
layout: archive
permalink: /archived-projects/
title: "Archived Projects"
author_profile: true
header:
  image: "/images/machinebanner.jpg"
---
{% include group-by-array collection=site.archivedposts field="tags" %}

{% for tag in group_names %}
  {% assign archivedposts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in archivedposts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
