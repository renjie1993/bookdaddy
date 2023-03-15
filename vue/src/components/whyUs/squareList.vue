<script setup>
import { content } from '@/content/squareList'
import Button from '../common/button.vue'

</script>

<template>
  <div class="square-list">
    <div class="square-item" v-for="item in content.list" :style="item.style">
      <img :src="item.imgSrc" width="250"/>
      <div class="desc">
        <h2 class="title">{{ item.title }}</h2>
        <div class="tip">{{ item.tip }}</div>
      </div>
    </div>
    <div class="square-center">
      <div class="title">{{ content.center.title }}</div>
      <div class="desc" v-html="content.center.desc"></div>
      <Button :link="content.center.href" :label="content.center.buttonLabel"></Button>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.square-list {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  position: relative;

  .square-item {
    width: 50%;
    height: 495px;
    box-sizing: border-box;

    img {
      padding: 25px;
    }

    &:nth-child(odd) {
      padding-left: 475px;
    }
    &:nth-child(even) {
      padding-left: calc(50% - 500px - 300px);
    }

    .desc {
      text-align: center;
      width: 300px;

      .title {
        color: #333;
        font-size: 24px;
        padding-bottom: 20px;
        font-weight: bold;
        margin: 0;
        line-height: 100%;
      }

      .tip {
        color: #333;
        font-size: 17px;
        line-height: 30px;
        text-align: left;
        vertical-align: baseline;
      }
    }
  }

  .square-center {
    background: url("whyus-center.png");
    width: 591px;
    height: 379px;
    position: absolute;
    z-index: 100;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    font-size: 18px;
    text-align: center;
    line-height: 30px;
    color: #333333;

    .title {
      margin-top: 115px;
    }

    .desc {
      margin-top: 5px;
    }

    .link {
      display: inline-block;
      background: #f16c5d;
      color: #ffffff;
      border-radius: 7px;
      padding: 5px 15px;
      margin-top: 10px;
      font-size: 18px;
    }
  }
}

</style>
