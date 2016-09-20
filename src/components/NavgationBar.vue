<template>
  <div :class="['navgation-bar', transparent ? 'navbar-light' : 'navbar-transparent']">
    <div class="navgation-bar-left">
      <div class="left-arrow" @click="onClickBack">
        <svg width="18px" height="18px" viewBox="0 0 19 36" version="1.1"><g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" stroke-linecap="round"> <g class="back-stroke" transform="translate(-30.000000, -32.000000)" stroke-width="2.6"> <path fill="" d="M47.5984706,66.2329397 L32.0875681,51.3636064 C31.4354381,50.7449397 31.4354381,49.7209397 32.0875681,49.1022731 L47.5984706,34.2329397"></path> </g> </g> </svg>
      </div>
    </div>
    <h1 class="navgation-bar-title" @click="$emit('on-click-title')">
      <span v-show="title">{{title}}</span>
    </h1>
  </div>
</template>

<script>

export default {
  ready () {
    
  },

  props: {
    transparent: {
      type: Boolean,
      required: true,
      twoWay: true
    },
    title: String,
  },

  data () {
    return {
      
    }
  },

  methods: {
    onClickBack() {
      console.log('navgation back item on clicked')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navgation-bar {
  position: fixed;
  height: 44px;
  width: 100%;
  max-width: 480px;
  
  z-index: 1;
}

.navbar-transparent {
  background-image: linear-gradient(rgba(0,0,0,.4) 20%,transparent);
}

.navbar-transparent path{
  stroke: #fff;
}
.navbar-light {
  background-color: #fff;
}

.navbar-light path {
  stroke: #ddbf91; 
}

.left-arrow {
  position: relative;
  width: 40px;
  height: 44px;
  line-height: 44px;
  text-align: center;
  z-index: 2;
}

</style>
