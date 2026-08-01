---
layout: archive
title: "Archive"
permalink: /archive/
author_profile: false
---

All {{ site.posts | size }} articles, newest first.

{% assign entries_layout = page.entries_layout | default: 'list' %}
<div class="entries-{{ entries_layout }}">
  {% include documents-collection.html entries=site.posts type=entries_layout %}
</div>
