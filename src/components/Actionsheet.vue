<template>
  <div class="yun-model-actionsheet">
    <!-- weui mask -->
    <div class="weui_mask_transition" :class="{'weui_fade_toggle': show}" :style="{display: show ? 'block' : 'none'}" @click="show=false"></div>
    <!-- weui actionsheet -->
    <div class="weui_actionsheet" :class="{'weui_actionsheet_toggle': show}" style="bottom:55px; background-color:white;max-width:480px;left:inherit;">
      <div class="drag-button" @click="toggle"></div>
      <!-- cells -->
      <div>
        <div v-for="item in tagItems" v-if="!subscribed">
          <div class="cell-tag">
            <div class="button-tag cell" :class="item.style">{{item.title}}</div>
            <p class="p-tag">{{item.content}}}</p>
          </div>
        </div>
      </div>
      <!-- subscribed view-->
      <div class="tips" v-if="subscribed">
        <p>
          <svg width="29px" height="29px" viewBox="346 794 58 58" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" _v-5d2d794f=""> <desc _v-5d2d794f="">Created with Sketch.</desc> <defs _v-5d2d794f=""></defs> <g id="Group" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" transform="translate(346.000000, 794.000000)" _v-5d2d794f=""> <rect id="Rectangle-830" fill="#282728" x="0" y="0" width="58" height="58" rx="29" _v-5d2d794f=""></rect> <path d="M26.7143129,36.8571088 C26.568029,36.8571088 26.421745,36.8011095 26.3103177,36.6896823 L19.2858299,29.6651945 L17.9755598,30.9754646 C17.7521339,31.1988905 17.3909953,31.1988905 17.1675694,30.9754646 C16.9441435,30.7520387 16.9441435,30.3909001 17.1675694,30.1674742 L18.8818347,28.4532089 C19.1052607,28.229783 19.4663992,28.229783 19.6898251,28.4532089 L26.7143129,35.4776967 L40.0244402,22.1675694 C40.2478661,21.9441435 40.6090047,21.9441435 40.8324306,22.1675694 C41.0558565,22.3909953 41.0558565,22.7521339 40.8324306,22.9755598 L27.1183081,36.6896823 C27.0068809,36.8011095 26.8605969,36.8571088 26.7143129,36.8571088 L26.7143129,36.8571088 Z" id="Shape" stroke="#DDBF91" fill="#DDBF91" _v-5d2d794f=""></path> </g> </svg>
        </p>
        <p>恭喜你代言成功</p>
        <p>赶紧去订购吧</p>
      </div>
      <!-- invite tips -->
      <div class="invite-button">邀请好友代言-拿20元补贴</div>
    </div>
  </div>
</template>

<script>

export default {
  ready () {
  },

  props: {
    show: {
      type: Boolean,
      required: true,
      twoWay: true
    },
    tagItems: {
      type: Array
    },
    subscribed: {
      type: Boolean,
      required: true,
      twoWay: true
    }
  },

  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
    }
  },

  methods: {
    toggle() {
      this.show = !this.show
    },
    subscribe() {
      this.subscribed = !this.subscribed
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less">
@import '../styles/weui/widget/weui_tips/weui_mask';
@import '../styles/weui/widget/weui_tips/weui_actionsheet';

.yun-model-actionsheet {
  background-color: white;
  z-index: 1001;
}

.drag-button {
  position: absolute;
  cursor: pointer;
  background-size: 47px 20px;
  width: 47px;
  height: 20px;
  top: -20px;
  left: 0; 
  right: 0; 
  margin-left: auto; 
  margin-right: auto; 
  background-image: url(../assets/grag.png) ;
  z-index: 1002;
}

.cell-tag {
  display: table;
  padding: 10px;
}

.button-tag {
  font-size: 12px;
  width: 90px;
  height: 35px;
  text-align: center;
  display: table-cell;
  vertical-align: middle;
}

.p-tag {
  padding: 10px;
  font-size: 12px;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}

.gold-button {
  background-color: #ddbf91;
  color: #6e5f48;
}

.silver-button {
  background-color: #e7e5e5;
  color: #737272;
}

.bronze-button {
  background-color: #f4ac6b;
  color: #795535;
}

.invite-button {
  margin-top: 40px;
  height: 35px;
  line-height: 35px;
  color: #797979;
  font-size: 16px;
  font-weight: 400;
  background-color: #f4f4f4;
  text-align: center;
}

.tips {
  height: 177px;
}

.tips p {
  color: #ddbf91;
  text-align: center;
  font-size: 20px;
}

.tips p:first-child {
  padding-top:30px;
}
.cell {
  display: table-cell;
  vertical-align: middle;
}
</style>
