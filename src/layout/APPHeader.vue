<template>
  <div class="header">
    <el-input v-model="input" size="large" class="w-50 m-2 search-input" placeholder="搜索分组、项目、接口..."
      :prefix-icon="Search" />
    <el-dropdown>
    <span class="el-dropdown-link">
      <div class="header-avatar">
        <el-avatar :size="30" :src="circleUrl" />
      <span class="user-name">小猫咪</span>
      <el-icon class="el-icon--right">
        <arrow-down />
      </el-icon>
      </div>
    </span>
    <template #dropdown>
      <el-dropdown-menu>
        <el-dropdown-item>Action 1</el-dropdown-item>
        <el-dropdown-item>Action 2</el-dropdown-item>
        <el-dropdown-item>Action 3</el-dropdown-item>
        <el-dropdown-item disabled>Action 4</el-dropdown-item>
        <el-dropdown-item divided>Action 5</el-dropdown-item>
      </el-dropdown-menu>
    </template>
  </el-dropdown>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Search, ArrowDown } from '@element-plus/icons-vue'
import { reactive, toRefs } from 'vue'

const input = ref('')

const circleUrl = ref('https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png');

</script>

<style scoped lang="less">
.header {

  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  background-color: transparent;
  border-radius: 0 20px 0 0;

  .search-input {
    height: 55px;
  }

  /deep/.el-input__wrapper {
    box-shadow: none;
    background-color: transparent;
  }

  .el-dropdown-link:focus-visible {
  outline: unset;
}

  .header-avatar {
    width: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    .user-name{
      margin-left: 10px;
      max-width: 60px;
    }
  }
}
</style>