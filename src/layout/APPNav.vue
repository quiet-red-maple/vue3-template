<template>
  <div class="app-nav">
    <ul>
      <li v-for="item in navList" :key="item.id">
        {{ item.title }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import { ArrowLeft } from '@element-plus/icons-vue'
const navList = reactive([
  {
    title: '返回',
    id: 1,
  },
  {
    title: '首页',
    id: 2,
  },
  {
    title: '用户管理',
    id: 3,
  }
]);



</script>

<style scoped lang="less">
.app-nav {
  background-color: white;
  height: 40px;
  line-height: 40px;
  padding-left: 20px;
  padding-right: 20px;

  ul {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    li {
      border-right: 1px solid #F5F5F5;
      padding-left: 10px;
      padding-right: 10px;
      font-size: 14px;
    }
    .disabled {
        color: #BABCBE;
      }
  }
}

.el-page-header {
  height: 100%;

  /deep/.el-page-header__header {
    height: 100%;
  }
}
</style>