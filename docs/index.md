---
layout: default
title: Главная
---

<section class="home-hero">
  <h1>Заметки о работе в IT, проектах и продуктах</h1>
  <p class="lead">
    Пишу о принятии решений, процесах, технологиях и практических наблюдениях из рабочих проектов.
  </p>
</section>

<section class="home-section">
  <div class="section-heading">
    <h2>Последние записи</h2>
  </div>

  <div class="post-list">
  {% for post in site.posts limit:5 %}
    <article class="post-card">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d.%m.%Y" }}</time>
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    </article>
  {% endfor %}
  </div>
</section>

<section class="contact-strip">
  <span>Есть вопрос или идея для разговора?</span>
  <div class="contact-links">
    <a href="mailto:pashilka@gmail.com">pashilka@gmail.com</a>
    <a href="https://t.me/whileAIworks" target="_blank" rel="noopener noreferrer">@whileAIworks</a>
  </div>
</section>
