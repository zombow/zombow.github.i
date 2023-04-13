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
    <!-- velog feed api -->
  <div id="feed"></div>
  <script>
    fetch('https://velogfeed.vercel.app/api/numfeed?username=dksduddnr33&postnum=0')
      .then(res => res.json())
      .then(feed => {
        let html = '';
          const item = feed;
          html += `<div>
                      <a href="${item.link}">${item.title}</a>
                      <p>${item.contentSnippet}</p>
                   </div>`;
        document.getElementById('feed').innerHTML = html;
      });
  </script>
  </div>
  <!-- velog feed api end -->
</section>
