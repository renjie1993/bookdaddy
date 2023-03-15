<script setup>
import { content } from '@/content/homeIntro'
import Button from "@/components/common/button.vue";
</script>

<template>
  <div class="home-intro">
    <div class="main-area">
      <div class="title">{{ content.title }}</div>
      <div class="desc" v-html="content.desc"></div>
      <Button class="button" :label="content.buttonLabel" :link="content.link"></Button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.home-intro {
  background: url("home-intro-bg.jpg") no-repeat;
  background-size: cover;
  min-height: 770px;
  text-align: left;
  position: relative;

  .main-area {
    width: 1600px;
    margin: 0 auto;
    padding-top: 60px;

    .title {
      font-size: 40px;
      color: #000;
      line-height: 100%;
      margin-top: 60px;
    }

    .desc {
      font-size: 17px;
      color: #000;
      line-height: 100%;
      max-width: 900px;
      margin: 60px 0;
      letter-spacing: 2px;
    }

    .button {
      padding: 12px 20px;
      font-size: 23px;
      position: absolute;
      left: 50%;
      bottom: 50px;
      transform: translateX(-50%);
    }
  }
}
</style>
