<script setup>
import { content } from "@/content/whyUs";
import SquareList from "./squareList.vue";
import HomeIntro from "./homeIntro.vue";
import HomeCate from "./homeCate.vue";
import HomeTutorial from "./homeTutorial.vue";

</script>

<template>
  <el-carousel class="whyus-carousel" type="card" :interval="12000" height="500">
    <el-carousel-item v-for="item in content.carouselList" :key="item">
      <div class="swiper-slide-text">{{ item.slideText[0] }}<br>{{ item.slideText[1] }}<br></div>
      <div class="swiper-slide-slogan">{{ item.slideSlogan }}</div>
      <img class="swiper-background" :src="item.imgSrc">
    </el-carousel-item>
  </el-carousel>

  <div class="feature-intro">
    <h1>{{ content.featureIntro }}</h1>
  </div>

  <SquareList></SquareList>
  <HomeCate></HomeCate>
  <HomeIntro></HomeIntro>
  <HomeTutorial></HomeTutorial>
</template>

<style lang="scss" scoped>
.whyus-carousel {
  height: 500px;
  margin-top: 6px;

  :deep(.el-carousel__container) {
    height: 100%;
  }

  .swiper-slide-text, .swiper-slide-slogan {
    width: 400px;
    height: 38px;
    position: absolute;
    top: 25%;
    left: 12%;
    text-align: left;
    font-size: 38px;
    line-height: 150%;
    color: #ffffff;
    font-weight: bold;
    text-shadow: 1px 1px 3px #585858;
    letter-spacing: 3px;
    user-select: none;
  }

  .swiper-slide-slogan {
    top: unset;
    bottom: 25%;
    font-size: 24px;
    padding-left: 50px;
    background: url('banner-logo-icon.png') center left no-repeat;
  }

  .swiper-background {
    position: absolute;
    top: 0;
    width: 100%;
    height: 500px;
    z-index: -1;
  }
  :deep(.el-carousel__indicators--outside.el-carousel__indicators) {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
  }
}

.feature-intro {
  padding: 30px 0;

  h1 {
    color: #666;
    text-align: center;
    font-size: 20px;
    line-height: 50px;
  }
}
</style>
