
<template>
  <div class="login" style="">
    <Button ghost>Default</Button>
    <Button type="primary" ghost>Primary</Button>
    <Button type="dashed" ghost>Dashed</Button>
    <Button type="text" ghost>Text</Button>
    <br><br>
    <Button type="info" ghost>Info</Button>
    <Button type="success" ghost>Success</Button>
    <Button type="warning" ghost>Warning</Button>
    <Button type="error" ghost>Error</Button>
    <br/>
    <Button type="primary" shape="circle" icon="ios-search">这是搜索框</Button>
    <Button shape="circle" icon="ios-search"></Button>
  </div>
</template>

<script>
    export default {
      name: "login",
    }
</script>

<style scoped>
  .login {
    width:400px;
    height:400px;
    background-color: silver ;
    margin: 0 30%;
    border: 1px solid black
  }
</style>

