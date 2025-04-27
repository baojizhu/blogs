---
title: Tags
layout: default
---

<div style="display: flex; flex-direction: row; gap: 20px;">
  <!-- 左侧：标签分类 -->
  <aside style="width: 25%; border-right: 1px solid #ccc; padding-right: 10px;">
    <h2>按标签分类的博客文章</h2>
    {% assign tags = site.tags %}
    <ul>
      {% for tag in tags %}
        <li>
          <a href="#{{ tag[0] }}">{{ tag[0] }}</a>
          <ul>
            {% for post in tag[1] %}
              <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
            {% endfor %}
          </ul>
        </li>
      {% endfor %}
    </ul>
  </aside>

  <!-- 右侧：所有博客文章 -->
  <main style="width: 75%; padding-left: 10px;">
    <h2>所有博客文章</h2>
    <ul>
      {% for post in site.posts %}
        <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
  </main>
</div>