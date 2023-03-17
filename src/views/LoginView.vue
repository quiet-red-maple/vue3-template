<template>
  <div id="page" class="site">
    <div class="container">
      <div class="login">
        <div class="hero">
          <h1>你好 世界<br>Hello World</h1>
          <p>如果你没有账号<br>可以<a href="#">点击这里</a>进行注册.</p>
        </div>
        <div class="main">

          <el-form ref="loginFormRef" :model="loginForm" :rules="rules" class="login-from">
            <el-form-item prop="userName">
              <el-input v-model="loginForm.userName" placeholder="账号" autocomplete="off" class="login-input" />
            </el-form-item>
            <el-form-item prop="passWord">
              <el-input v-model="loginForm.passWord" type="password" placeholder="密码" autocomplete="off" class="login-input" show-password/>
              <a href="#" class="give-password">找回密码</a>
            </el-form-item>
            <el-form-item class="login-button-box">
              <el-button type="primary" class="sub-btn" @click="submitForm(loginFormRef)">登录</el-button>
            </el-form-item>
          </el-form>
          <div class="options">
            <div class="separator">
              <p>使用其他方式登录</p>
            </div>
            <ul>
              <li><a href="#"><i class="ri-steam-fill ri-2x"></i></a></li>
              <li><a href="#"><i class="ri-playstation-fill ri-2x"></i></a></li>
              <li><a href="#"><i class="ri-xbox-fill ri-2x"></i></a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue';
import { LoginFromType } from '../types/login';
import type { FormInstance } from 'element-plus';
import { useRouter } from 'vue-router';

const router = useRouter();

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
      router.push({
        name: 'home',
      });
    } else {
      console.log('error submit!')
      return false
    }
  })
}
</script>

<style lang="less" scoped>
.give-password {
  position: absolute;
  right: 20px;
  bottom: -17px;
  font-size: 13px;
  color: var(--light-text-color);
  height: 20px;
  gap: 10px;

  :hover {
    color: var(--dark-color);
    text-decoration: underline;
  }
}

.login-button-box {
  margin-top: 20px;
}

/*用中文替换原先英文字体*/

.site {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.container {
  max-width: 1000px;
  width: 100%;
  padding: 0 30px;
  margin: 0 auto;
}

.login {
  display: flex;
  flex-wrap: wrap;
}

.hero {
  flex: 1 0 66.6666%;
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 50px;
  padding: 70px 0;
}


@keyframes myfirst {
  0% {
    background: linear-gradient(to right, var(--primary-color), #c471ed, #f64f59);
  }

  33% {
    background: linear-gradient(to right, var(--primary-color), #c471ed, #f64f59);
    left: 200px;
    top: 0px;
  }

  66% {
    background: linear-gradient(to right, var(--primary-color), #c471ed, #f64f59);
    left: 200px;
    top: 200px;
  }

  100% {
    background: linear-gradient(to right, var(--primary-color), #c471ed, #f64f59);
  }
}

.hero::before {
  content: '';
  position: absolute;
  top: 15%;
  left: 0;
  width: 280px;
  height: 100px;
  background: linear-gradient(to right, var(--primary-color), #c471ed, #f64f59);
  z-index: -1;
  filter: blur(70px);
  animation: myfirst 100s infinite;
  -webkit-animation: myfirst 100s infinite;
  /* Safari 与 Chrome */
}

.hero a {
  font-weight: 500;
  color: var(--primary-color);
  transition: color .3s;
}

.hero a:hover,
form .password a:hover {
  color: var(--dark-color);
  text-decoration: underline;
}

.main {
  flex: 1 0 33.3333%;
}

.main form {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.main form p {
  position: relative;
}

input {
  font: inherit;
  font-size: 14px;
  width: 100%;
  border: 0;
  outline: 0;
  padding: 0 20px;
  line-height: 60px;
  border-radius: 10px;
  /*修复input 加入padding之后大小变化的问题*/
  box-sizing: border-box;
}

.login-input {
  height: 60px;
  border-radius: 10px;
  background-color: var(--light-bg-color);
  background-color: red;
}

/deep/.el-input__wrapper {
  background-color: var(--light-bg-color);
  border-radius: 10px;
}

/deep/input::placeholder {
  color: var(--dark-color);
  font-family: 'Noto Sans SC', sans-serif;
  font-size: inherit;
}

input:not(.submit) {
  background-color: var(--light-bg-color);
}

.password i {
  position: absolute;
  top: calc(60px / 2);
  right: 20px;
  margin-top: -8px;
  line-height: 1;
  color: var(--light-text-color);
  cursor: pointer;
}

.password a {
  font-size: 13px;
  color: var(--light-text-color);
  float: right;
  margin: 5px 20px 0 0;
}

input.submit {
  font-weight: 700;
  color: var(--white-color);
  background-color: var(--primary-color);
  box-shadow: var(--primary-color) 0 20px 30px -10px;
  cursor: pointer;
  transition: box-shadow .3s;
}

input.submit:hover {
  box-shadow: var(--primary-color) 0 10px 30px -10px;
}

.sub-btn {
  width: 100%;
  height: 60px;
  border-radius: 10px;
  border: none;
  font-weight: 700;
  color: var(--white-color);
  background-color: var(--primary-color);
  box-shadow: var(--primary-color) 0 20px 30px -10px;
  cursor: pointer;
  transition: box-shadow .3s;
}

.sub-btn.submit:hover {
  box-shadow: var(--primary-color) 0 10px 30px -10px;
}

.separator {
  position: relative;
  margin: 50px 0 30px;
}

.separator::before {
  content: '';
  position: absolute;
  top: 50%;
  width: 100%;
  height: 1px;
  background-color: var(--light-text-color);
  opacity: .3;
  z-index: 1;
}

.separator p {
  font-size: 14px;
  width: fit-content;
  padding: 0 10px;
  color: var(--light-text-color);
  background-color: var(--background-color);
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.options ul {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.options ul li a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  border-radius: 10px;
  background-color: var(--white-color);
  box-shadow: var(--light-text-color) 0 10px 20px -10px;
  transition: all .3s ease-out;
}

.options ul li a:hover {
  color: var(--white-color);
  box-shadow: none;
}

/*用STEAM PSN XBOX替换原先APPLE GOOGLE FACEBOOK图标*/
.options ul li:nth-child(1) a:hover {
  background-color: #171a21;
}

.options ul li:nth-child(2) a:hover {
  background-color: #00439c;
}

.options ul li:nth-child(3) a:hover {
  background-color: #107c10;
}</style>