

<script type="text/javascript">
   import '../assets/js/bootstrap.min.js'

   export default {
    props:['msg'],
    ready () {
        $('.carousel').carousel()
     }
   }
</script>

<template>
    <div id="myCarousel" class="carousel slide">
           <ol class="carousel-indicators">
             <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
             <li data-target="#myCarousel" data-slide-to="1"></li>
             <li data-target="#myCarousel" data-slide-to="2"></li>
           </ol>
           <!-- Carousel items -->
           <div class="carousel-inner">
             <div class="active item"><img src="http://file20.mafengwo.net/M00/1C/08/wKgB3FDZPLeAMsDyABQR1ettz4k09.jpeg" :title="msg[0]"></div>
             <div class="item"><img src="http://www.zhlzw.com/lz/UploadFiles_1767/201302/20130224020532375.jpg" :title="msg[1]"></div>
             <div class="item"><img src="http://att.bbs.duowan.com/forum/201208/07/1522579g92nn4wwg1f2s99.jpg" :title="msg[2]"></div>
           </div>
           <!-- Carousel nav -->
           <a class="carousel-control left" href="#myCarousel" data-slide="prev">&lsaquo;</a>
           <a class="carousel-control right" href="#myCarousel" data-slide="next">&rsaquo;</a>
      </div>
</template>