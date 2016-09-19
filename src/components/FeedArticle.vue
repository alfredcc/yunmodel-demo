<template>
  <div class="feed-articles">
    <!-- feed card header -->
    <div class="feed-card-header">
      <label class="title col">麻豆卖家秀</label>
      <label class="meta col">共 {{modelCount}} 位麻豆</label>
    </div>
    <!-- feed article list -->
    <div class="feed-card-article-list" v-for="article in articles">
      <div class="feed-card-article">
        <!-- author info -->
        <div class="feed-card-article-author">
          <div class="author-info">
            <div class="author-info-avatar">
              <img :src="article.avatar" alt="">
            </div>
            <div class="author-info-detail col">
              <div class="author-name">{{article.author}}</div>
              <div class="author-rank"><span class="badge" style="background-image: url(http://igeek.coding.me/demos/yumodel/1.png);"></span>{{article.rank}}</div>
            </div>
          </div>
          <div class="body-info">{{article.bodyInfo}}</div>
        </div>
        <!-- article content -->
        <div class="feed-card-article-content">{{article.content}}</div>
        <!-- image scroller -->
        <scroller lock-y scrollbar-x :bounce=true>
          <div :style="[scrollStyle, { width: article.imageURLs.length * (350 + 5) - 5 +'px'}]">
            <div class="feed-card-article-image-item" v-for="imgURL in article.imageURLs">
              <img :src="imgURL">
            </div>
          </div>
        </scroller>
      </div>
    </div>
    <div class="feed-card-bottom">已显示全部</div>
  </div>
</template>

<script>

import { Scroller } from 'vux/src/components/'

export default {
  ready () {
    console.log(this.articles.length)
    console.log(this.modelCount)
  },

  components: {
    Scroller
  },
  props: {
    modelCount: {
      type: Number,
      default: 0
    },
    articles: {
      type: Array,
      default() {
        return[]
      }
    }
  },

  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      scrollStyle: {
          height: '340px',
          position: 'relative',
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.feed-card-header {
  display: flex;
  align-items: center;
  padding: 12px;
  border-bottom: 1px solid #f1f1f1;
  background-color: white;
}

.feed-card-bottom {
  margin: auto;
  padding: 0px 0px 12px 0px;
  text-align: center;
  color: #aaa;
  font-size: 16px;
}

.feed-card-header .title {
  color: #ddbf91;
  font-size: 14px;
  font-weight: 700;
}

.feed-card-header .meta {
  color: #666;
  font-size: 12px;
  text-align: right;
  vertical-align: middle;
}

.feed-card-article {
  background-color: white;
  margin-bottom: 10px;
}

.feed-card-article-author {
  display: flex;
  flex-direction: column;
  height: 60px;
  width: auto;
  padding: 12px;
}

.author-info {
  height: 60px;
  display: flex;
}

.author-info-avatar {
  border-radius: 50%;
  background-color: #f8f8f8;
  width: 35px;
  height:35px;
  margin-right: 10px;
  overflow: hidden;
}

.body-info {
  color: #b2b2b2;
  font-size: 12px;
  padding-top: 10px;
}

.author-name {
  font-size: 14px;
}

.author-rank {
  display: flex;
  align-items: center;
  font-size: 12px;
  color: rgb(204, 0, 255);
}

.badge {
  display: inline-block;
  background-size: contain;
  background-repeat: no-repeat;
  height: 14px;
  width: 14px;
}

.feed-card-article-content {
  font-size: 14px;
  padding: 0px 12px 12px 12px;
}

.feed-card-article-image-item {
  width: 350px;
  height: 90%;
  background-color: #ccc;
  display:inline-block;
  margin-left: 5px;
  float: left;
  text-align: center;
  line-height: 100px;
}
.feed-card-article-image-item:first-child {
  margin-left: 0px;
}

.col {
  flex:1;
}
</style>
