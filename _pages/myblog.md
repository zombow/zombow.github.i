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
        const url = postinfo.url;
        const cardHtml = `
          <div style="text-align: center;">
            <a href="${url}" target="_blank">${postinfo.svg}</a>
          </div>
        `;
        feedElement.innerHTML += cardHtml;
      });
      const svgs = document.querySelectorAll('#feed svg');
      svgs.forEach(svg => {
        const newWidth = 100;
        const newHeight = 50;
        const viewBoxAttr = svg.getAttribute('viewBox');
        const viewBoxValues = viewBoxAttr.split(' ');
        const svgWidth = parseFloat(viewBoxValues[2]);
        const svgHeight = parseFloat(viewBoxValues[3]);
        const widthRatio = newWidth / svgWidth;
        const heightRatio = newHeight / svgHeight;
        const newViewBox = `0 0 ${svgWidth * widthRatio} ${svgHeight * heightRatio}`;
        svg.setAttribute('viewBox', newViewBox);
        svg.setAttribute('width', newWidth);
        svg.setAttribute('height', newHeight);
      });
    })
    .catch(error => console.error(error));
</script>

<!-- velog feed api end -->

