<script setup>
import suggestion from './suggestion.vue'
import { content } from '@/content/footer'
</script>

<template>
  <suggestion></suggestion>
  <div class="footer">
    <div class="main-area">
      <div class="title">
        <img :src="content.imgSrc">
      </div>
      <div class="menu-list">
        <div class="menu-item" v-for="menu in content.menuList">
          <div class="menu-item-title">
            <a :href="menu.title.link">{{ menu.title.label }}</a>
          </div>
          <div class="menu-inner">
            <div class="menu-item-title inner" v-for="innerItem in menu.list">
              <a :href="innerItem.link">{{ innerItem.label }}</a>
            </div>
          </div>
        </div>
      </div>
      <div class="remarks">
        <div class="remark-item" v-for="item in content.remarks">
          <div class="label" v-if="item.type === 'label'">{{ item.value }}</div>
          <a class="link" v-if="item.type === 'link'" :href="item.link">
            <component :is="item.prefixIcon" width="18" style="transform: translateY(4px)"></component>
            <span>{{ item.value }}</span>
          </a>
        </div>
      </div>
      <div class="copyright">{{ content.copyright }}</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer {
  color: #ffffff;
  padding-top: 40px;
  background: #666666;

  img {
    transition: all 0.5s;
    height: 50px;
    margin-top: 10px;
  }

  .main-area {
    width: 1600px;
    margin: 0 auto;

    .menu-list {
      display: flex;

      .menu-item {
        width: 20%;
        margin-bottom: 10px;
        letter-spacing: 1px;

        .menu-item-title {
          a {
            color: #ffffff;
            font-size: 22px;
            border-bottom: 2px solid #fff;
          }
        }
        .inner {
          margin: 15px 0;
          width: 100%;

          a {
            border-bottom: none;
            font-size: 15px;

            &:hover {
              text-decoration: underline;
            }
          }
        }
      }
    }

    .remarks {
      .label, .link {
        padding: 5px;
      }
      .link {
        font-size: 14px;

        span {
          margin-left: 2px;
        }
      }
    }

    .copyright {
      padding: 30px 0;
      text-align: center;
    }
  }
}
</style>
