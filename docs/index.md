---
layout: default
title: Обо мне
---

# 👋 Привет!

Я использую этот сайт как личный блог / портфолио / сайт.

## 📝 Последние записи

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> — <small>{{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>

---

📬 Связаться со мной: [pashilka@gmail.com](mailto:pashilka@gmail.com)
