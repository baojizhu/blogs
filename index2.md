---
title: Tags
layout: default
---
<script>
  document.addEventListener("DOMContentLoaded", function () {
    const toggles = document.querySelectorAll(".tag-toggle");
    toggles.forEach(toggle => {
      toggle.addEventListener("click", function () {
        const content = this.nextElementSibling;
        if (content.style.display === "none" || !content.style.display) {
          content.style.display = "block";
        } else {
          content.style.display = "none";
        }
      });
    });
  });
</script>
<div style="display: flex; flex-direction: row; gap: 20px;">
  <!-- 左侧：标签分类 -->
  <aside style="width: 25%; border-right: 1px solid #ccc; padding-right: 10px;">
    <h2>按标签分类的博客文章</h2>
    {% assign tags = site.tags %}
    <ul>
      {% for tag in tags %}
        <li>
          <button class="tag-toggle" style="background: none; border: none; color: blue; cursor: pointer;">{{ tag[0] }}</button>
          <ul style="display: none;">
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