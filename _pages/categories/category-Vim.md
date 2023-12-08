---
title: "Vim"
layout: archive
permalink: categories/Vim
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['Vim'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
