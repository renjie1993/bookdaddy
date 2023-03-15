<script setup>
import { content } from "@/content/suggestion.js";

</script>

<template>
  <div class="suggestion">
    <div class="main-area">
      <div class="title">{{ content.title }}</div>
      <div class="slogan-list">
        <a v-for="item in content.sloganList" :href="item.link">
          <img :src="item.imgSrc + '.webp'">
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.suggestion {
  color: #ffffff;
  background: #f8f7f5;
  padding: 40px;

  .main-area {
    width: 1600px;
    margin: auto;
    color: #333333;
    font-size: 12px;
  }

  .title {
    font-size: 20px;
    margin-bottom: 20px;
    color: #666666;
    text-shadow: 1px 1px 0 #d2d4d6;
  }

  .slogan-list {
    a {
      display: inline-block;
      width: 18%;
      margin: 0 1%;

      img {
        height: 70px;
      }
    }
  }
}
</style>
