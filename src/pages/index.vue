<template>

  <div class="web">

    <div class="main">
      <carousel-item :banner="banner" class="m1"></carousel-item>
      <card-item class="m2"></card-item>
    </div>

  </div>

</template>

<script>
import CarouselItem from "../components/CarouselItem.vue";
import CardItem from "../components/CardItem.vue";
export default {
  name: "index",
  components: {
    'carousel-item': CarouselItem,
    'card-item': CardItem
  },
  data() {
    return {
      banner: [
        {
          text: "1. 第一图片",
          src: require("../assets/img/1.jpg")
        },
        {
          text: "2. 第一张片",
          src: require("../assets/img/2.png")
        },
        {
          text: "3. 第一张图",
          src: require("../assets/img/3.jpeg")
        },
        {
          text: "3. 一张图片",
          src: require("../assets/img/4.jpg")
        }
      ]
    };
  }
};
</script>

<style>
body {
    margin: 0;
    padding: 0;
  }
  .web {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  .left {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .main {
    display: flex;
    position: relative;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }
  .right {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .m1 {
    transition: all 0.2s ease-in-out;
    height: 20rem;
  }
  .m2 {
    transition: all 0.2s ease-in-out;
    height: 22rem;
  }
  
  
  @media only screen and (min-width: 320px) {
    html {
      font-size: 14px !important;
    }
  }
  @media only screen and (min-width: 360px) {
    html {
      font-size: 15.7px !important;
    }
  }
  @media only screen and (min-width: 375px) {
    html {
      font-size: 16.4px !important;
    }
  }
  @media only screen and (min-width: 375px) and (min-height: 812px) {
    html {
      font-size: 20px !important;
    }
  }
  @media only screen and (min-width: 400px) {
    html {
      font-size: 18px !important;
    }
  }
  @media only screen and (min-width: 411px) {
    html {
      font-size: 18px !important;
    }
  }
  @media only screen and (min-width: 411px) and (min-height: 823px) {
    html {
      font-size: 20.3px !important;
    }
  }
  @media only screen and (min-width: 414px) {
    html {
      font-size: 18.2px !important;
    }
  }
  @media only screen and (min-width: 480px) {
    html {
      font-size: 18px !important;
    }
  }
  @media only screen and (min-width: 540px) {
    html {
      font-size: 18px !important;
    }
  }
  @media only screen and (min-width: 640px) {
    html {
      font-size: 18px !important;
    }
  }
  @media only screen and (min-width: 768px) {
    html {
      font-size: 25.3px !important;
    }
  }
  @media only screen and (min-width: 960px) {
    html {
      font-size: 23px !important;
    }
  }
  @media only screen and (min-width: 1024px) and (min-height: 1366px) {
    html {
      font-size: 33.8px !important;
    }
  }
  
  @media only screen and (min-width: 1200px) {
    html {
      font-size: 25px !important;
    }
    .main {
      transition: all 0.2s ease-in-out;
      width: 70%;
    }
  }
</style>


