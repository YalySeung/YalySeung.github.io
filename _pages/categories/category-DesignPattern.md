---
title : "디자인 패턴"
layout : archive
permaling : categories/DesignPattern
author_profile : true
sidebar_main : true
---


{% assign posts = site.categories['Design Pattern'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}