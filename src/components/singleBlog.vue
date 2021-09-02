<template>
<div>
<div class="jumbotron jumbotron-fluid">
  <div class="container">
    <h1 class="display-8">{{blog.title | to-uppercase}}</h1>
    <p>Author - {{blog.author}}</p>
    <p class="lead">{{blog.content}}</p>
    <hr>
    <p>Categories:</p>
    <ul>
        <li v-for="i in blog.categories">{{i}}</li>
    </ul>
  </div>
</div>
</div>

</template>

<script>

export default {
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
    },
    created(){
        this.$http.get('https://blog-vue-app-9a3c8-default-rtdb.firebaseio.com/posts/' + this.id +'.json/').then(function(data){
            return data.json()
        }).then(function(data){
            this.blog=data;
            
        })
    }
 
}
</script>

<style scoped>

</style>
