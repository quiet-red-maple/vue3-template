<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="280">
        <APPMenu/>
      </el-aside>
      <el-container>
        <el-header style="{padding: 0}">
          <APPHeader/>
        </el-header>
        <el-nav style="{padding: 0}">
          <APPNav/>
        </el-nav>
        <el-main>
          <APPMan/>
        </el-main>
        <!-- <el-footer>Footer</el-footer> -->
      </el-container>
    </el-container>
  </div>
</template>

<script setup lang="ts">
import APPMenu from './APPMenu.vue';
import APPHeader from './APPHeader.vue';
import APPNav from './APPNav.vue';
import APPMan from './APPMan.vue';

</script>

<style lang="less" scoped>

.el-header{
  padding: 0;
  border: 0;
  height: 55px;
}

.el-main{
  background-color: white;
  margin: 20px;
  border-radius: 5px;
}
</style>