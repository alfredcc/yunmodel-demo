<template>
  <div id="app">
    <!-- section navgation -->
    <div id="section-nav">
      <div style="height:100%;">
        <x-header style="background-color:#"></x-header>
      </div>
    </div>
    <!-- section header -->
    <div id="section-header">
      <swiper :loop="true" dots-class="custom-bottom" :show-desc-mask="false" height="500px" dots-position="center" auto>
          <swiper-item class="swiper-video">
            <video preload="auto"  controls="true" src="http://static.yunmadou.13980.com/Upload/movie/anessa750_2.mp4" poster="http://static.yunmadou.13980.com/Upload/movie/%E5%AE%89%E5%A5%88%E5%97%AE%E7%85%A7%E7%89%87.jpg@740_-100d"></video>
          </swiper-item>
          <swiper-item class="swiper-demo-img">
            <img src="http://static.yunmadou.13980.com/Upload/movie/index1.png@740w">
          </swiper-item>
      </swiper>
      <!-- intro -->
      <div class="intro">
        <div class="intro-title">{{title}}</div>
        <div class="intro-price">  
          <label class="intro-discount-price">全国统一零售价：{{discountPrice}}</label>
          <label class="intro-origin-price">同类市场价：{{originPrice}}</label>
        </div>
        <div class="muted">
          <svg width="13px" height="13px" viewBox="0 0 32 32" version="1.1"> <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" opacity="0.5"> <g transform="translate(-83.000000, -305.000000)" fill="#000000"> <g transform="translate(83.000000, 121.000000)"> <path d="M16.0157604,216.009029 C14.6311928,216.009029 13.2362269,215.82746 11.859658,215.457922 C3.33788835,213.173505 -1.73645992,204.384581 0.547156774,195.864411 C1.6533711,191.736304 4.30012684,188.286483 8.00110564,186.150041 C11.7028843,184.0128 16.0141607,183.446495 20.140668,184.551909 C28.6616378,186.834726 33.7359861,195.624451 31.4531692,204.145421 C31.0620349,205.605976 30.4557366,207.013739 29.6534713,208.332718 C29.42311,208.708655 28.9319924,208.828635 28.5536559,208.599873 C28.1761193,208.369512 28.0569393,207.876794 28.2865007,207.500058 C29.0103792,206.311457 29.5558877,205.04367 29.9078286,203.73189 C30.9028616,200.016514 30.3925473,196.136365 28.46967,192.804924 C26.5467928,189.475083 23.4417139,187.092283 19.7271374,186.09645 C16.0117611,185.102217 12.1324122,185.611732 8.80097138,187.535409 C5.47033042,189.458286 3.08753037,192.563365 2.09249739,196.277941 C0.0376422957,203.946254 4.60407582,211.857726 12.2731886,213.912581 C16.1069451,214.941209 20.0950757,214.359706 23.500904,212.279255 C23.8776408,212.048894 24.3695582,212.168874 24.6007194,212.544811 C24.8310807,212.922347 24.7111009,213.414265 24.3343641,213.644626 C21.773194,215.208364 18.9160736,216.009029 16.0157604,216.009029 L16.0157604,216.009029 Z M15.9997631,204.80371 C16.441289,204.80371 16.7996288,205.16205 16.7996288,205.603576 L16.7996288,207.203307 C16.7996288,207.644833 16.441289,208.003173 15.9997631,208.003173 C15.5582372,208.003173 15.1998973,207.644833 15.1998973,207.203307 L15.1998973,205.603576 C15.1998973,205.16205 15.5582372,204.80371 15.9997631,204.80371 L15.9997631,204.80371 Z M16.0005629,202.404913 C15.5582372,202.404913 15.2006972,202.046573 15.2006972,201.604247 L15.2006972,192.805724 C15.2006972,192.364198 15.5582372,192.006658 16.0005629,192.006658 C16.4420888,192.006658 16.8004287,192.364198 16.8004287,192.805724 L16.8004287,201.604247 C16.8004287,202.046573 16.4420888,202.404913 16.0005629,202.404913 L16.0005629,202.404913 Z"></path> </g> </g> </g> </svg>
          <span class="muted-content">本产品由品牌商源头直供，去除所有中间商环节</span>
        </div>
      </div>
    </div>
    
    <!-- feed article -->
    <feed-article :articles="articles" :model-count="modelCount"></feed-article>

    <!-- <div :class="isActionSheetHidden ? 'weui_mask_transition' : 'weui_mask'" v-on:click="hideActionSheet"></div> -->
    <actionsheet :show.sync="show"></actionsheet>

    <div class="bottom-action">
        <div class="button-block">代言该产品</div>
    </div>
</template>


<script>
import FeedArticle from './components/FeedArticle'
import Actionsheet from './components/Actionsheet'

import {XHeader, Swiper, SwiperItem, Scroller } from 'vux/src/components/'

const dataSource = {
  list: [
  'http://static.yunmadou.13980.com/Upload/movie/index1.png@740w',
  'http://static.yunmadou.13980.com/Upload/movie/%E9%A6%96%E5%9B%BE2.png@740w',
  'http://static.yunmadou.13980.com/Upload/movie/%E9%A6%96%E5%9B%BE3.png@740w'
  ],
  intro: {
    title: '资生堂安耐晒',
    originPrice:'899元',
    discountPrice: '255元',
  },
  modelCount: 2,
  articleList: [{
    author: '大白',
    avatar: 'http://static.yunmadou.13980.com/Upload/movie/lADOZQAeiM0IoM0E2g_1242_2208.jpg@50h',
    rank: '明星麻豆',
    bodyInfo: '身高：170cm 体重：48kg 胸围：92 腰围：60 臀围：92',
    content: '我是敏感皮肤，之前用防晒容易闷痘，试了下薄薄的很水润，这几天都没有出痘痘，以后防晒就靠它了。',
    imageURLs: [
    'http://static.yunmadou.13980.com/Upload/movie/lADOZQAeg80FAM0DwA_960_1280.jpg@340h_350w_1e_1c',
    'http://static.yunmadou.13980.com/Upload/movie/lADOZQAeh80FAM0DwA_960_1280.jpg@340h_350w_1e_1c',
    'http://static.yunmadou.13980.com/Upload/movie/lADOZQAehc0IoM0E2g_1242_2208.jpg@340h_350w_1e_1c',
    'http://static.yunmadou.13980.com/Upload/movie/lADOZQAeiM0IoM0E2g_1242_2208.jpg@340h_350w_1e_1c'
    ]
  },
  {
    author: '汪隐',
    avatar: 'http://static.yunmadou.13980.com/Upload/movie/IMG_2714.JPG@50h',
    rank: '明星麻豆',
    bodyInfo: '身高：170cm 体重：48kg 胸围：92 腰围：60 臀围：92',
    content: '用了两年了，夏天防晒确实靠得住。完全晒不黑什么的是扯淡，但效果还是挺明显的。',
    imageURLs: [
    'http://static.yunmadou.13980.com/Upload/movie/IMG_2714.JPG@340h_350w_1e_1c',
    'http://static.yunmadou.13980.com/Upload/movie/IMG_2715.JPG@340h_350w_1e_1c'
    ]
  }
  ]
}

export default {
  data() {

    return {
      show: true,
      isActionSheetHidden: false,
      list: dataSource.list,
      title: dataSource.intro.title,
      discountPrice: dataSource.intro.discountPrice,
      originPrice: dataSource.intro.originPrice,
      articles: dataSource.articleList,
      modelCount: dataSource.modelCount
    }
  },
  components: {
    XHeader,
    Swiper,
    SwiperItem,
    FeedArticle,
    Actionsheet
  },
  methods: {
    hideActionSheet() {
      this.isActionSheetHidden = !this.isActionSheetHidden
    }
  }
}
</script>

<style>
#app {
  margin: auto;
  width: 100%;
  max-width: 480px;
  height: 100%;
  background-color: #f1f1f1
}

#section-header {
  background-color: white;
  margin-bottom: 10px;
}
.swiper-video img {
  height: 400px;
}

.swiper-img img {
  width: 100%;
}

.intro-title {
  padding: 10px;
  font-size: 17px;
  font-weight: 700;
}
.intro-price {
  padding-left: 10px;
  display: flex;
}

.intro-discount-price {
  flex: 1;
  font-size: 14px;
}

.intro-origin-price {
  font-size: 14px;
  color: #999;
  flex: 1;
  text-align: right;
  margin-right: 10px;
}

.muted {
  display: flex;
  align-items: center;
  color: #999;
  font-size: 12px;
  padding: 10px;
}

.muted-content {
  margin-left: 10px;
}

.bottom-action {
  position: fixed;
  bottom: 0px;
  max-width: 480px;
  width: 100%;
  z-index: 10000;
  background-color: white;
}
/* 垂直居中 */
.button-block {
  margin: 10px;
  height: 35px;
  line-height: 35px;
  color: #fff;
  background-color: #ddbf91;
  text-align: center;
}
</style>
