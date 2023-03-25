<template>
  <router-view/>
</template>

<style lang="less">
*{
  margin: 0;
  padding: 0;
}

html,body,#app {
  width:100%;
  height: 100%;
  background-color: var(--bg-color-right);
}

* {
  margin: 0;
  padding: 0;
}

*,
::before::after {
  box-sizing: border-box;
}

body {
  font-family: 'Noto Sans SC', sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.8;
  color: var(--dark-color);
  background-color: var(--background-color);
  user-select: none;
  -webkit-user-drag: none;
}

a {
  text-decoration: none;
  color: inherit;
  -webkit-tap-highlight-color: transparent;
}

ul {
  list-style: none;
}

h1 {
  font-size: 3em;
  font-weight: 700;
  line-height: normal;
  color: black;
}
</style>
