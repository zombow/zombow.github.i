---
layout: myblog
title: My Blog
---

<section class="section">
  <div class="container">
     <!--구 벨로그 api
     <div class="row">
      {% for post in site.posts offset:0 limit:6%} <!--이 post가 읽어들인 마크다운파일
      {% include mypost.html %}
      {% endfor %}
    </div>
    구벨로그 api끝-->

<!-- velog feed api -->

<div id="feed" style="display: grid; grid-template-columns: repeat(2, 1fr); justify-content: center; align-items: center; grid-row-gap: 80px; grid-column-gap: 50px;"></div>
<script>
  fetch('https://velogfeed.vercel.app/api/feed?username=dksduddnr33&postnum=6')
    .then(res => res.json())
    .then(postinfoList => {
      const feedElement = document.getElementById('feed');
      
      postinfoList.forEach((postinfo, index) => {
        const svg = postinfo.svg;
        const url = postinfo.url;

        const cardHtml = `
          <div style="text-align: center;">
            <a href="${url}">${svg}</a> <!-- postcard 위치 -->
          </div>
        `;

        feedElement.innerHTML += cardHtml;
      });
    })
    .catch(error => console.error(error));
</script>


<!-- velog feed api end -->

  </div>
</section>

