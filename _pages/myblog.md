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
  <div id="feed"></div>
  <script>
    fetch('https://velogfeed.vercel.app/api/feed?username=dksduddnr33')
      .then(res => res.json())
      .then(feed => {
        let html = '';
        for (let i = 0; i < feed.items.length; i++) {
          const item = feed.items[i];
          html += `<div>
                      <a href="${item.link}">${item.title}</a>
                      <p>${item.contentSnippet}</p>
                   </div>`;
        }
        document.getElementById('feed').innerHTML = html;
      });
  </script>
  </div>
</section>
