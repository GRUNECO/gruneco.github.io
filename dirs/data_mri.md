---
title : MRI
---
# MRI

<ul>
   {% for item in site.data.data_mri-list %}
      <li><a href="{{ item.link }}">{{ item.title }}</a></li>
      {% if item.frame %}
      <img src="{{item.frame}}">
      {% endif %}
   {% endfor %}
</ul>