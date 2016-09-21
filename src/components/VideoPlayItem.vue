<template>
  <div class="swiper-video-item">
    <video preload="auto"  src="http://static.yunmadou.13980.com/Upload/movie/anessa750_2.mp4" poster="http://static.yunmadou.13980.com/Upload/movie/%E5%AE%89%E5%A5%88%E5%97%AE%E7%85%A7%E7%89%87.jpg@740_-100d" id="product-video"></video>
    <div class="video-play-action" @click="playVideo">
      <div v-if="showVideoAction">
        <h1>NO.1</h1>
        <h2>比防晒霜效果好太多了</h2>
        <h3>滋生安耐晒</h3>
        <p>
          <svg width="51px" height="51px" viewBox="326 485 102 102" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"> <g id="Play-Copy-2" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" transform="translate(327.000000, 486.000000)"> <path d="M50,100 C77.6142375,100 100,77.6142375 100,50 C100,22.3857625 77.6142375,0 50,0 C22.3857625,0 0,22.3857625 0,50 C0,77.6142375 22.3857625,100 50,100 L50,100 Z" id="Oval-89" stroke="#FFFFFF" stroke-width="2" opacity="0.3"></path> <path d="M40.6539427,67.9178205 L40.6539427,32.092021 L69.0410179,50.0041255 L40.6539427,67.9178205 L40.6539427,67.9178205 L40.6539427,67.9178205 Z M71.2247614,47.7010952 L41.3076344,28.2064526 C39.5326469,27.2410249 37.5,27.6720478 37.5,30.8116761 L37.5,69.1981653 C37.5,72.3155268 39.6805625,72.870608 41.3076344,71.8017984 L71.2247614,52.3087463 C72.9488532,51.0872495 72.9011385,48.8239815 71.2247614,47.7010952 L71.2247614,47.7010952 L71.2247614,47.7010952 Z" id="Fill-126" fill="#FFFFFF"></path> </g> </svg>
        </p>
        {{videoDuration}}s'
        <div>
          <p class="product-meta-price">￥ {{productInfo.price}} 元</p>
          <p class="product-meta-tag">{{productInfo.tag}}</p>
          <p class="product-meta-remain">{{productInfo.remain}}剩余名额</p>
        </div>
      </div>
    </div>
  <div>
</template>

<script>
export default {
  ready () {
    this.getVideoTime()
  },

  props: {
    productInfo: {
      type: Object,
      required: true,
      twoWay: true
    }
  },

  data () {
    return {
      showVideoAction: true,
      videoDuration: 0.0
    }
  },

  methods: {
    playVideo() {
      this.showVideoAction = false
      let video = document.getElementById("product-video")
      video.play()
      video.onended = function (e){
        this.showVideoAction = true
      }.bind(this)
    },
    getVideoTime() {
      let video = document.getElementById("product-video")
      video.onloadeddata = function (e){
        this.videoDuration =  Math.ceil(video.duration)
      }.bind(this)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.video-play-action {
  position: absolute;
  left: 50%;
  width: 100%;
  color: #fff;
  max-width: 480px;
  top: 50%;
  text-align: center;
  transform: translate(-50%,-50%);
}

.swiper-video-item video {
  max-width: 480px;
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.video-play-action h1, h2, h3, p {
  font-size: 22px;
  font-weight: 300;
  color: #fff;
  text-align: center;
}

.video-play-action h1 {
  margin-bottom: 30px;
}

.video-play-action h3 {
  font-size: 18px;
  margin-bottom: 30px;
}

.product-meta-price {
  font-size: 18px;
}

.product-meta-tag {
  display: inline-block;
  font-size: 10px;
  width: auto;
  padding: 2px 6px;
  border: 1px solid hsla(0,0%,100%,.6);
  border-radius: 100px;
  margin-bottom:20px;
}

.product-meta-remain {
  font-size: 15px;
}
</style>
