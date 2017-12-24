安装
```
npm i -save waterripple
或
yarn add waterripple
```
使用
```
<template>
  <WaterRipple class="login-box" @onClick="login" text="登陆"></WaterRipple>
</template>

<script>
  import WaterRipple from 'waterripple'
  export default {
    components: {
      WaterRipple
    },
    methods: {
      login (password) {
        console.log('点击了！')
      }
    }
  }
</script>

<style scoped>
  .login-box {
      height: 400px;
      width: 500px;
      background-color: rgba(0, 0, 0, 0.2);
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      margin: auto;
    }
</style>
```

效果

![Alt text](http://puge-10017157.cossh.myqcloud.com/github8600/%E6%B0%B4%E6%B3%A2%E7%BA%B9.gif)
