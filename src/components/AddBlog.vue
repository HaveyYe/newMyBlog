<template>
  <div id="add-blog">
    <h2>添加博客</h2>
    <form v-if="submited">
      <label>博客标题</label>
      <input type="text" v-model="blog.title" required/>
      <label>博客内容</label>
      <textarea v-model="blog.content"> </textarea>
      <div id="checkboxes">
        <label> Vue.js</label>
        <input type="checkbox" value="Vue.js" v-model="blog.categories"/>
        <label> Node.js</label>
        <input type="checkbox" value="Node.js"  v-model="blog.categories"/>
        <label> React.js</label>
        <input type="checkbox" value="React.js"  v-model="blog.categories"/>
        <label> Angular4</label>
        <input type="checkbox" value="Angular4"  v-model="blog.categories"/>
      </div>
      <label>作者</label>
      <select id="author" v-model="blog.author">
        <option v-for="author in authors">
          {{author}}
        </option>
      </select>
    </form>

     <div v-if="!submited">
       <h3>您的博客发布成功</h3>
     </div>

    <button @click.stop="post">添加博客</button>
    <hr>

    <div id="preview">
      <h3>博客总览</h3>
      <p>博客标题：{{blog.title}}</p>
      <p>博客内容</p>
      <p>{{blog.content}}</p>
      <p>博客分类</p>
      <ul>
        <li v-for="category in blog.categories">
                {{category}}
        </li>
      </ul>
      <p>作者：{{blog.author}}</p>
    </div>
  </div>
</template>

<script>
  //下面内容是初始化LeanCloud
  var AV = require('leancloud-storage');
  var APP_ID = 'HyfNKzDrMlpWL5zFR0Gh17hv-gzGzoHsz';
  var APP_KEY = 'dnMvPdduOl9DH3QTncNya9Cb';
  AV.init({
    appId: APP_ID,
    appKey: APP_KEY
  });
  var blog = AV.Object.extend('blog')
    export default {
      //https://jsonplaceholder.typicode.com/这是一个很好的用的前端测试接口网站
        name: "add-blog",
      data(){
          return{
            blog:{
              title:"",
              content:"",
              categories:[],
              author:""
            },
            authors:["阿斗","刘备","曹操","孙权"],
            submited:true
          }
      },
      methods:{
          post:function () {
     /*       var acl =new AV.ACL();
            acl.setPublicReadAccess(true)
            acl.setPublicWriteAccess(true)
        /!*    acl.setReadAccess(true)
            acl.setWriteAccess(true)*!/*/
            new blog({
              title:this.blog.title,
              content:this.blog.content,
              categories:this.blog.categories,
              author:this.blog.author,
            }).save().then(function(blog) {

            }.bind(this)).catch(alert)
                this.submited=false;
          }
      }
    }

    /* this.$http.post("https://jsonplaceholder.typicode.com/posts",{
       title:this.blog.title,
       body:this.blog.content,
       userId:1
     }).then(function(data){
       this.submited=false;
       console.log(data);
     })*/
</script>

<style scoped>
#add-blog *{
  box-sizing: border-box;
}
  #add-blog{
    margin:20px auto;
    max-width:600px;
    padding:20px;
  }

  label{
    display: block;
    margin:20px 0 10px;
  }
  input[type="text"],textarea,select{
    display: block;
    width:100%;
    padding:8px;
  }
  textarea{
    height:200px;
  }
  #checkboxes label{
    display: inline-block;
    margin-right:0px;
  }
#checkboxes input{
  display: inline-block;
  margin-right:10px;
}
 button{
   display: block;
   margin:20px 0;
   background: crimson;
   color: #fff;
   border:0;
   padding:14px;
   border-radius: 4px;
   font-size: 18px;
   cursor: pointer;
 }
  #preview{
    padding:10px 20px;
    border:1px dotted #ccc;
    margin:30px 0;

  }
  h3{
    margin-top:10px;
  }
</style>
