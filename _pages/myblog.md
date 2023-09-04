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
  fetch('https://velogfeed.vercel.app/api/feed?username=dksduddnr33&postnum=0')
.then(res => res.json())
    .then(postinfo => {
      const svg = postinfo.svg;
      const url = postinfo.url;
      const post = postinfo.post;
      const html = `
        <div>
          <a href="${url}">${svg}</a>
        </div>
      `;
      document.getElementById('feed').innerHTML = html;
    })
    .catch(error => console.error(error));
</script>

<!-- velog feed api end -->

  </div>
</section>

