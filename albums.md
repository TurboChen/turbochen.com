---
title: "Albums"
permalink: /albums/
---

<html>

  {% include head.html %}
  
  <body>
  
    {% include header.html %}
    
    <div class="page-content">
      <div class="wrapper">
      
        <header class="post-header">
          <h1 class="post-title">{{ page.title }}</h1>
        </header>
        
        <!-- 安静 -->
        <embed class="album-player" src="http://www.xiami.com/widget/46264100_39245211_250_346_5695c1_457cb4_0/collectPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        <!-- 姚贝娜 -->
        <embed class="album-player" src="http://www.xiami.com/widget/46264100_39868737_250_346_333333_999999_0/collectPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        <!-- 精选集 -->
        <embed src="http://www.xiami.com/widget/46264100_38828539_250_346_800000_008080_0/collectPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        <!-- Jason Marz - Yes! -->
        <embed src="http://www.xiami.com/widget/46264100_1773198549,1773198563,1773215220,1773237249,1773198553,1773198554,1773198555,1773198556,1773198557,1773288371,1773301074,1773261317,1773198561,1773198562,_250_346_666699_bfe5e8_0/multiPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        <!-- Jason Marz - MR.A-Z -->
        <embed src="http://www.xiami.com/widget/46264100_2079004,2079005,2079006,2079007,2079008,2079009,2079010,2079011,2079012,2079013,2079014,2079015,1769884403,1769884404,1769884405,1769884406,_250_346_5695c1_c0c0c0_0/multiPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        <!-- Jason Marz - Love Is a Four Letter Word -->
        <embed src="http://www.xiami.com/widget/46264100_1770830897,1770830898,1770830899,1770830900,1770830901,1770830902,1770830903,1770830904,1770830905,1770830906,1770830907,1770830908,1770941465,1770941466,1770941467,1770941468,1770941469,1770941470,_250_346_d90000_000080_0/multiPlayer.swf" type="application/x-shockwave-flash" width="250" height="346" wmode="opaque"></embed>
        
        
        
        <!--
        <ul class="album-list">
          {% for album in site.data.albums %}
            <li class="album-list">
            
              <div class="album-left">
                <a href="{{ album.link }}">
                  <img class="album-image" src="/images/albums/{{ album.album-image }}" alt="{{ album.name }}"></img>
                </a>
              </div>
              
              <div class="album-right">
                {{ album.player }}
                <p class="album-name">{{ album.name }}</p>
                <p class="album-info">{{ album.author }} - {{ album.date }} - {{ album.record-compnay }}</p>
                <p class="album-brief">{{ album.brief }}</p>
              </div>
            </li>
          {% endfor %}
        </ul>
        -->
        
      </div>
    </div>
    
    {% include footer.html %}

  </body>

</html>