---
title: "CleanCode"
layout: archive
permalink: categories/CleanCode
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['CleanCode'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
