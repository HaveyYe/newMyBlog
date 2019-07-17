<template>
    <div id="single-blog" @click="fetchBlog">
      <div v-if="show">
        <span id="blog">aaa</span>
        <h1>标题:{{title}}</h1>
        <article>{{blog.content}}</article>
        <h2>作者：{{blog.author}}</h2>
        <h3>分类
          <span v-for="categorie in blog.categories">
            {{categorie}}
          </span>
        </h3>
      </div>
      <div v-if="!show">
        没有找到相关信息
      </div>
    </div>
</template>

<script>
  var AV = require('leancloud-storage');
  var blog = AV.Object.extend('blog');
    export default {
      name: "single-blog",
      data() {
        return {
          id: this.$route.params.id,
          blog: {},
          title: "",
          show: true,
        }
      },
      created() {
        var query = new AV.Query('blog');
        query.equalTo("objectId",this.id);
        query.find().then(function (messages) {
          let array = messages.map((item) => item.attributes);
          array.forEach((item) => {
            //this.blog=item;
            let li = document.createElement('li')
            li.innerText = item.content;
            let messageList = document.querySelector('#single-blog')
            messageList.appendChild(li)
          })
        })
      },
      methods: {}
    }
</script>

<style scoped>
#single-blog{
  max-width: 960px;
  margin:0  auto;
  padding:20px;
  background:#eee;
  border:1px dotted #aaa;
}

</style>
