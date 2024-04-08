---
layout: myblog
title: My Blog
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Blog</title>
  <style>
    #feed {
        display: flex;
        flex-wrap: wrap;
        justify-content: center; /* 가로 간격을 균등하게 분배하여 정렬 */
        column-gap:30px;
        row-gap: 50px;
    }
    @media screen and (max-width: 1000px) {
    #feed {
        display: flex;
        justify-content: center; /* 가로 간격을 균등하게 분배하여 정렬 */
      }
    }

  </style>
</head>
<body>

<section class="section">

<!-- velog feed api -->

<div id="feed"></div>
<script>
  fetch('https://velogfeed.vercel.app/api/feed?username=dksduddnr33&postnum=6')
    .then(res => res.json())
    .then(postinfoList => {
      const feedElement = document.getElementById('feed');
      postinfoList.forEach((postinfo) => {
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

