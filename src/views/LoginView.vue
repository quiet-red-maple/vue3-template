<template>
  <div class="login-box">
    <el-form ref="loginFormRef" :model="loginForm" status-icon :rules="rules" label-width="70px" class="login-from">
      <h1>后台管理系统</h1>
      <el-form-item label="账号：" prop="userName">
        <el-input v-model="loginForm.userName" autocomplete="off" />
      </el-form-item>
      <el-form-item label="密码：" prop="passWord">
        <el-input v-model="loginForm.passWord" type="password" autocomplete="off" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" class="sub-btn" @click="submitForm(loginFormRef)">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue';
import { LoginFromType } from '../types/login';
import type { FormInstance } from 'element-plus';


const loginFormRef = ref<FormInstance>()

const loginForm: LoginFromType = reactive({
    userName: '',
    passWord: '',
});

const rules = {
  userName: [
    { required: true, message: '请输入账号', trigger: 'blur' },
    { min: 6, max: 24, message: '账号长度需要在6-24之间', trigger: 'blur' },
  ],
  passWord: [
    { required: true, message: '请输入密码', trigger: 'blur' },
    { min: 6, max: 24, message: '密码长度需要在6-24之间', trigger: 'blur' },
  ]
};

const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.validate((valid) => {
    if (valid) {
      console.log('submit!', valid, loginForm)
    } else {
      console.log('error submit!')
      return false
    }
  })
}
</script>

<style lang="less" scoped>
.login-box {
  width: 100%;
  height: 100%;
  padding-top: 200px;
  background: red;

  .login-from {
    width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: white;
    border-radius: 20px;

    h1 {
      margin-left: 50px;
      text-align: center;
      padding-bottom: 20px;
    }

    .sub-btn {
      width: 100%;
    }
  }
}
</style>