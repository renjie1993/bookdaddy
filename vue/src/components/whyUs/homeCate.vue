<script setup>
import { content } from '@/content/homeCate'
import {ref} from "vue";

const currentIndex = ref(0)

const handleMenuChange = (index) => {
  currentIndex.value = index
}

</script>

<template>
  <div class="home-cate">
    <div class="header">
      <span class="title">{{ content.title }}</span>
      <a class="button" :href="content.href">{{ content.hrefLabel }}</a>
    </div>
    <div class="home-cate-content">
      <div class="menu">
        <div class="menu-item" v-for="(item, index) in content.navs" @click="handleMenuChange(index)" :class="{ active: index === currentIndex }">{{ item.title }}</div>
      </div>
      <div class="category">
        <div class="cate-item" v-for="item in content.navs[currentIndex].list">
          <img :src="item.imgSrc" />
          <div class="cate-item-label">{{ item.label }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.home-cate {
  background: #f9f9f9;
  margin: 0 auto;
  padding: 60px 0;
  box-sizing: border-box;
  min-height: 1000px;

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 2%;
    margin: 0 auto 20px auto;
    width: 1600px;

    .title {
      font-size: 35px;
      color: #222;
      line-height: 100%;
    }

    .button {
      color: #ffffff;
      font-size: 22px;
      background: #10567b;
      padding: 13px 20px;
      border-radius: 5px;
    }
  }

  .home-cate-content {
    width: 1650px;
    margin: 0 auto;

    .menu {
      float: left;
      width: 20%;
      border-left: 1px solid #f0f0f0;

      .menu-item {
        font-size: 18px;
        padding: 12px 0 12px 15px;
        cursor: pointer;
        user-select: none;

        &.active, &:hover {
          border-left: 5px solid #f16c5d;
          color: #f16c5d;
          font-weight: bold;
        }
      }
    }

    .category {
      float: right;
      width: 75%;
      display: flex;
      flex-wrap: wrap;

      .cate-item {
        box-shadow: 2px 2px 5px #e5e5e5;
        margin: 15px;
        width: calc(33.33% - 30px);
        overflow: hidden;
        height: 230px;
        position: relative;
        border-radius: 5px;
        cursor: pointer;

        img {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          transition: all 0.7s;

          &:hover {
            transform: scale(1.1);
          }
        }

        .cate-item-label {
          position: absolute;
          bottom: 0;
          left: 0;
          line-height: 50px;
          background: #ffffff;
          width: 100%;
          padding: 0 10px;
          color: #666666;
          font-size: 17px;
        }
      }
    }
  }
}
</style>
