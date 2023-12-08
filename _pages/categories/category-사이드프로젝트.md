---
title: "사이드프로젝트"
layout: archive
permalink: categories/사이드프로젝트
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['사이드프로젝트'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
