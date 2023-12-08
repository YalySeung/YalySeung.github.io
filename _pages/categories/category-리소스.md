---
title: "리소스"
layout: archive
permalink: categories/리소스
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['리소스'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
