<template>
  <div class="yun-model-actionsheet">
    <!-- weui_mask -->
    <div class="weui_mask_transition" :class="{'weui_fade_toggle': show}" :style="{display: show ? 'block' : 'none'}" @click="show=false"></div>
    <!-- weui actionsheet -->
    <div class="weui_actionsheet" :class="{'weui_actionsheet_toggle': show}" style="bottom:55px; background-color:white">
      <div class="drag-button" @click="toggle"></div>
      <!-- cells -->
      <div>
        <div class="cell-tag">
          <div class="button-tag gold-button cell">金牌批发</div>
          <p class="p-tag">￥130/50件起 或 明星麻豆1件起拿</p>
        </div>
        <div class="cell-tag">
          <div class="button-tag silver-button">银牌批发</div>
          <p class="p-tag">￥130/50件起 或 明星麻豆1件起拿</p>
        </div>
        <div class="cell-tag">
          <div class="button-tag bronze-tag cell">铜牌批发</div>
          <p class="p-tag">￥130/50件起 或 明星麻豆1件起拿</p>
        </div>
      </div>
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
  // position: fixed;
  z-index: 1001;
}

.drag-button {
  position: absolute;
  background-repeat:no-repeat;
  cursor: pointer;
  border:0px;
  background-size: 43px 16px;
  width: 43px;
  height: 16px;
  top: 0px;
  left: 50%;
  margin-right: -22px;
  margin-top: -16px;
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

.bronze-tag {
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


.cell {
  display: table-cell;
  vertical-align: middle;
}
</style>
