<template>
<div id="show-blog">
    <h1>All blogs</h1>
    <input type="text" class="form-control" id="exampleFormControlInput1" placeholder="SEARCH BLOGS" v-model="search" />
    <div id="single-blog" v-for="blog in filteredBlogs">
      
        <div class="jumbotron jumbotron-fluid">
           <div class="container">
           <h3 class="display-8">{{blog.title | to-uppercase}}</h3>
           <p class="lead">{{blog.content | snippet}}</p>
             <router-link v-bind:to="'/blog/' + blog.id"><button type="button" class="btn btn-outline-dark">View blog</button></router-link>
          </div>
        </div>
        

        
    </div>

</div>

</template>

<script>

export default {
 
  data () {
    return {
     blogs:[],
     search:''
    }
  },
  created(){
      this.$http.get('https://blog-vue-app-9a3c8-default-rtdb.firebaseio.com/posts.json').then(function(data){
          return data.json();
      }).then(function(data){
          var blogsArray=[];
          for (let key in data){
              data[key].id=key
              blogsArray.push(data[key])
          }
          this.blogs=blogsArray
      })
  },
  computed:{
      filteredBlogs:function(){
          return this.blogs.filter((blog)=>{   //iterates thro each blog
              return blog.title.match(this.search); //return boolean
          })
      }
  }
}
</script>

<style scoped>
h1{
    text-align: center;
    margin-top: 2%;
}
#show-blog{
    margin:0% 10%;
}
.form-control{
    margin:3% 0%;
}
</style>
