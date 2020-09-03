---
  layout: archive
  title: "Data Science Posts by Tags"
  permalink: /datascience/
  author_profile: true
  header:
    image: "/assets/images/cbus_night.jpg"
---

{% include group-by-array collection=site.posts field="tags" %}
{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
