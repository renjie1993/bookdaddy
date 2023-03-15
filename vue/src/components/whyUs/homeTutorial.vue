<script setup>
import { content } from '@/content/homeTutorial'
</script>

<template>
  <div class="home-tutorial">
    <div class="main-area">
      <div class="title">{{ content.title }}</div>
      <div class="container">
        <div class="item" v-for="(item, index) in content.process">
          <div class="inner-content">
            <img :src="item.imgSrc">
            <div class="item-title">
              {{ index + 1 }}&nbsp;
              <img src="slash.webp">
              &nbsp;{{ item.title }}
            </div>
            <div class="desc">{{ item.desc }}</div>
          </div>
          <div class="arrow-right">
            <DArrowRight v-if="index !== (content.process.length - 1)" color="#f16c5d" width="35"></DArrowRight>
          </div>
        </div>
      </div>
      <div class="button-group">
        <Button class="button" v-for="item in content.buttonGroup" :link="item.href" :label="item.text" :showIcon="false"></Button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.home-tutorial {
  padding: 60px 0;

  .main-area {
    width: 1700px;
    margin: 0 auto;

    .title {
      font-size: 35px;
      color: #222222;
      text-align: center;
      line-height: 100%;
    }

    .container {
      display: flex;
      flex-wrap: nowrap;
      padding: 70px 0;

      .item {
        width: 25%;
        position: relative;

        .inner-content {
          display: flex;
          justify-content: center;
          flex-wrap: wrap;

          & > img {
            width: 200px;
            height: 200px;
          }

          .item-title {
            color: #10567b;
            font-size: 27px;
            line-height: 120%;
            margin: 30px 0 15px 0;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
          }

          .desc {
            color: #000;
            font-size: 17px;
            line-height: 150%;
            text-align: center;
            max-width: 280px;
          }
        }

        .arrow-right {
          position: absolute;
          right: 0;
          top: 90px;
        }
      }
    }

    .button-group {
      text-align: center;
      .button {
        font-size: 23px;
        border-radius: 7px;
        margin: 0 20px;
      }
    }
  }
}
</style>
