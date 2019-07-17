<template xmlns:v-theme="http://www.w3.org/1999/xhtml">
    <div v-theme:column="'narrow'" id="show-blog">
      <h1>博客总览</h1>
      <input type="text" v-model="search" placeholder="搜索">
      <div v-for="blog in filterBlogs" class="single-blog">
       <router-link v-bind:to="'/blog/'+blog.objectId">
         <h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
       </router-link>
        <article>{{blog.content | sinippet}}</article>
        <article>分类：{{blog.categories | sinippet}}</article>
      </div>
    </div>
</template>

<script>
  var AV = require('leancloud-storage');
  var blog = AV.Object.extend('blog')
    export default {
        name: "show-blog",
      data(){
          return{
            blogs:[],
            search:"",
          }
      },
      created() {
        const query = new AV.Query(blog)
         /* this.$http.get('./../static/posts.json')
            .then(function(data){
              //console.log(data);
              this.blogs=data.body.slice(0,10);
            })*/
         const updateBlogs=this.updateBlogs.bind(this);
        AV.Promise.all(query.find().then(updateBlogs));
      },
      computed:{
          filterBlogs:function () {
            return this.blogs.filter((blog)=>{
              return blog.title.match(this.search)
            })

          }
      },
      //局部自定义过滤器
      filters: {
        /*  "to-uppercase":function (value) {
            return value.toUpperCase();
          }*/
        toUppercase:function (value) {
          return value.toUpperCase();
        }
      },
      //局部的自定义指令
      directives:{
          /*'rainbow':{
            bind(el,bindling,vnode){
              el.style.color='red';
            }
          }*/
      },
      methods:{
        updateBlogs: function(blogs) {
          this.blogs = blogs.map(function(blog) {
            return blog.toJSON()
          })
          return blogs
        },
      }

    }
</script>

<style scoped>
#show-blog{
  max-width: 800px;
  margin:0 auto;
}
  .single-blog{
    padding:20px;
    margin:20px 0;
    box-sizing:border-box;
    background: #eee;
    border:1px dotted #aaa
  }
#single-blogs a{
  color: #444;
  text-decoration: none;
}
input[type="text"]{
  padding:8px;
  width:100%;
  box-sizing: border-box;

}
</style>
