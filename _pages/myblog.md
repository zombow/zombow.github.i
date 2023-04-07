---
layout: myblog
title: My Blog
---
<section class="section">
  <div class="container">
    <div class="row">
      {% for post in site.posts offset:0 limit:6%} <!--이 post가 읽어들인 마크다운파일-->
      {% include mypost.html %}
      {% endfor %}
    </div>
  </div>
</section>
