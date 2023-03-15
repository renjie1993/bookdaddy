<script setup>
import { content } from '@/content/header'
defineProps({
  msg: String,
})

const notificationNums = 0

</script>

<template>
  <div class="header">
    <div class="logo-container">
      <a href="https://www.bookdaddy.hk/zh-hk">
        <img class="logo" src="/logo.svg">
      </a>
      <div class="search-bar">
        <input type="text" :placeholder="content.searchBarPlaceholder"/>
        <img class="search-icon" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABUAAAAWCAMAAAAYXScKAAAAM1BMVEUAAACQpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK2QpK0Qb4MYAAAAEHRSTlMAECAwQFBgcICPn6+/z9/vIxqCigAAAH1JREFUGNOtkcsOwzAIBNeJ48Q2DfP/X9tL/ZLSQ6VyWo0WFoT0n4oVuHNYYAE3Az8W6ElSuCB2eOCf1sTdqQ1HITU5GXZKVzYiut4eqfApODdZOUfwMSJ8bytMwxJcmxQN5uOSA4D3LklSOM2sJpUVj+Ne4Sf89IGcv/3mDeIkBTpjbn6iAAAAAElFTkSuQmCC">
      </div>
    </div>
    <ul class="nav">
      <li class="menu-li" v-for="item in content.navigationList">
        <div class="menu-title">
          <component v-if="item.icon" :is="item.icon" style="width: 15px;"></component>
          {{ item.title }}
          <component v-if="item.list && item.list.length > 0" is="caretBottom" style="width: 15px;"></component>
        </div>
        <ul class="inner-menu" v-if="item.list">
          <li class="menu-li-inner" v-for="childNav in item.list">
            <component :is="childNav.icon" style="width: 15px;"></component>
            {{ childNav.text }}
          </li>
        </ul>
      </li>
      <li class="menu-li member-center">
        <a class="member-center-link">会员中心</a>
      </li>
      <li class="notification">
        <component is="iphone" style="width: 24px;"></component>
        <span class="notification-numbers">{{ notificationNums }}</span>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.header {
  box-sizing: border-box;
  background: #ffffff;
  width: 100%;
  height: 75px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  position: sticky;
  top: 0;
  z-index: 999;
  padding: 0 200px;
}

.logo-container {
  display: flex;
  align-items: center;
  width: 530px;
}

.search-bar {
  margin-left: 20px;
  padding: 0 20px;
  position: relative;

  .search-icon {
    position: absolute;
    top: 50%;
    right: 0;
    transform: translate(-150%, -50%);
  }

  input {
    width: 300px;
    height: 35px;
    font-size: 12px;
    background: #fafafa;
    box-shadow: 0 1px 2px rgba(0,0,0,.1) inset;
  }
}

.logo {
  width: 170px;
  height: 50px;
}

.nav {
  display: flex;
  align-items: center;
  height: 75px;
  width: 725px;
  margin: 0;

  .menu-li {
    padding: 0 12px;
    height: 75px;
    line-height: 75px;

    &:hover .inner-menu {
      display: block;
      animation-name: triggerOut;
      animation-duration: 0.5s;
    }
  }

  .menu-title {
    position: relative;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;

    &:hover {
      color: #555555;
    }
  }

  .inner-menu {
    box-shadow: 0 1px 5px -1px #ccc;
    background: #ffffff;
    position: absolute;
    display: none;
    cursor: pointer;

    .menu-li-inner {
      height: 40px;
      line-height: 16px;
      border-bottom: 1px solid #cccccc;
      box-sizing: border-box;
      width: 250px;
      padding: 12px 15px;
      &:hover {
        font-weight: bold;
        color: #555555;
      }
    }
  }

  .member-center {
    margin-left: 14px;
  }

  .member-center-link {
    background: #10567b;
    background-image: url('member-center.png');
    background-position: 7px center , 0 0;
    background-repeat: no-repeat , repeat-x;
    border-radius: 10px;
    color: #fff;
    font-size: 16px;
    height: 42px;
    padding: 10px 8px 10px 40px;
  }

  .notification {
    display: flex;
    align-items: center;

    .notification-numbers {
      color: #ffffff;
      height: 20px;
      line-height: 20px;
      transform: translate(-4px, -12px);
      font-size: 14px;

      &:before {
        content: '';
        background: #e00909;
        display: block;
        border-radius: 50%;
        height: 18px;
        width: 18px;
        position: absolute;
        z-index: -2;
        transform: translateX(-4px);
      }
    }
  }

  @keyframes triggerOut {
    0% {
      opacity: 0;
    }

    100% {
      opacity: 1;
    }
  }
}
</style>
