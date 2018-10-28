<template>
  <div class="carousel" 
  @mousedown="pointStart($event)" @mousemove="pointMove($event)" @mouseup="pointEnd($event)" @touchstart="pointStart($event)" @touchmove="pointMove($event)" @touchend="pointEnd($event)">
    <transition-group name="fade">
      <div v-for="(item, index) in banner" :key="index" v-show="index===currentIndex">
        <img :src="item.src" :alt="item.text" class="banner">
      </div>
    </transition-group>
    <!-- 左右切换按钮 -->
    <!-- <a class="carousel-control-prev" :class="{'prev-icon':prevActive}" @touchstart="movePrev" @click="movePrev">
      <span class="carousel-control-prev-icon"></span>
    </a>
    <a class="carousel-control-next" :class="{'next-icon':nextActive}" @touchstart="moveNext" @click="moveNext">
      <span class="carousel-control-next-icon"></span>
    </a> -->
    <!-- 指示符 -->
    <ul class="carousel-i">
      <li v-for="(item, index) in banner.length" :key="index" :class="{'active':index===currentIndex}" @click="change(index)"></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "carousel",
  props: ["banner"],
  data: function() {
    return {
      currentIndex: 0,
      autoTimer: null,
      prevActive: false,
      nextActive: false,
      count: 0,
      startX: 0,
      startY: 0,
      endX: 0,
      endY: 0
    };
  },

  methods: {
    change: function(i) {
      this.currentIndex = i;
    },
    moveNext: function() {
      if (this.currentIndex < this.banner.length - 1) {
        this.currentIndex++;
      } else {
        this.currentIndex = 0;
      }
      this.nextActive = true;
      setTimeout(() => {
        this.nextActive = false;
      }, 500);
    },
    movePrev: function() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      } else {
        this.currentIndex = this.banner.length - 1;
      }
      this.prevActive = true;
      setTimeout(() => {
        this.prevActive = false;
      }, 500);
    },
    autoplay: function() {
      this.currentIndex++;
      if (this.currentIndex >= this.banner.length) {
        this.currentIndex = 0;
      }
    },

    start: function() {
      this.autoTimer = setInterval(this.autoplay, 5000);
    },
    stop: function() {
      clearInterval(this.autoTimer);
    },

    pointStart: function(e) {
      e.preventDefault();
      this.startX = e.clientX || e.targetTouches[0].clientX;
      this.startY = e.clientY || e.targetTouches[0].clientY;
      clearInterval(this.autoTimer);
    },

    pointMove: function(e) {
      e.preventDefault();
    },

    pointEnd: function(e) {
      e.preventDefault();
      this.endX = e.clientX || e.changedTouches[0].clientX;
      this.endY = e.clientY || e.changedTouches[0].clientY;
      var moveX = this.endX - this.startX;
      var moveY = this.endY - this.startY;
      if (moveX < 0) {
        if (this.currentIndex < this.banner.length - 1) {
            this.currentIndex++;
          } else {
          this.currentIndex = 0;
           }
        } else if (moveX > 0) {
        if (this.currentIndex > 0) {
              this.currentIndex--;
            } else {
              this.currentIndex = this.banner.length - 1;
        }
      }
       this.autoTimer = setInterval(this.autoplay, 5000);
    }
  },
  mounted() {
    this.start();
  }
};
</script>

<style scoped>
@import "./css/carousel.css";
</style>

