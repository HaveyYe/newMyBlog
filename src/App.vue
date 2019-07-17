<template>
  <div id="app">
    <blog-header></blog-header>
  <!--  <img src="./assets/logo.png" @click="show=!show">-->
<!--    <login></login> &lt;!&ndash;// 显示组件&ndash;&gt;-->
<!--    <add-blog></add-blog>-->
<!--    <show-blog></show-blog>-->
    <router-view></router-view>
  </div>
</template>

<script>
  import AddBlog from "@/components/AddBlog";
  import ShowBlog from './components/ShowBlog'
  import BlogHeader from './components/BlogHeader'
  import login from './components/login' // 引入login.vue组件
  export default {
    name: 'App',
    components: {
      AddBlog,
      "login":login,
      ShowBlog,
      BlogHeader,
    },
  }
/*  //下面内容是初始化LeanCloud
  var AV = require('leancloud-storage');
  var APP_ID = 'HyfNKzDrMlpWL5zFR0Gh17hv-gzGzoHsz';
  var APP_KEY = 'dnMvPdduOl9DH3QTncNya9Cb';
  AV.init({
    appId: APP_ID,
    appKey: APP_KEY
  });*/
/*  var TestObject = AV.Object.extend('TestObject');
  var testObject = new TestObject();
  testObject.save({
    words: 'Hello World!'
  }).then(function(object) {
    alert('LeanCloud Rocks!');
  })*/
</script>

<style>
#app {
/*  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;*/
}

</style>
