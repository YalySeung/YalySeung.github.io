---
title: "할일"
layout: archive
permalink: categories/할일
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['할일'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
