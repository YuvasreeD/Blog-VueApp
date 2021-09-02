<template>
  <div id="add-blog">
    <h2 style="text-align:center;">Add Blog</h2>
    <form v-if="!submitted">
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Title</label>
        <input
          type="text"
          class="form-control"
          id="exampleFormControlInput1"
          v-model.lazy="blog.title"
        />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlTextarea1" class="form-label">Content</label>
        <textarea
          class="form-control"
          id="exampleFormControlTextarea1"
          rows="3"
          v-model.lazy="blog.content"
        ></textarea>
      </div>
      <div class="form-check">
          <input class="form-check-input" type="checkbox" id="flexCheckDefault" value="Food" v-model="blog.categories"/>
          <label class="form-check-label" for="flexCheckDefault">Food</label>
      </div>
      <div class="form-check">
          <input class="form-check-input" type="checkbox" id="flexCheckDefault" value="Science" v-model="blog.categories"/>
          <label class="form-check-label" for="flexCheckDefault">Science</label>
      </div>
      <div class="form-check">
          <input class="form-check-input" type="checkbox" id="flexCheckDefault" value="Technology" v-model="blog.categories"/>
          <label class="form-check-label" for="flexCheckDefault">Technology</label>
      </div>
      <br>
      <label>Author: </label>
      <select v-model="blog.author">
          <option v-for="author in authors">{{author}}</option>
      </select>
      <br><br>
      <button type="button" class="btn btn-dark" v-on:click.prevent="post() ">Add blog</button>
  
      
    </form>
    <div v-if="submitted">Thanks for writing your blog</div>
    <hr>
    <div>
      <p>Preview:</p>
      <p>Blog Title: {{ blog.title }}</p>
      <p>Blog Content: {{ blog.content }}</p>
      <p>Blog Categories:</p>
      <ul>
          <li v-for="i in blog.categories">{{i}}</li>
      </ul>
      <p>Author: {{blog.author}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blog: {
        title: "",
        content: "",
        categories:[],
        author:""
      },
      authors:['Yuvasree','Haritha','Indra','Dakshinamurthy'],
      submitted:false
    };
  },
  methods:{
      post(){
          this.$http.post('https://blog-vue-app-9a3c8-default-rtdb.firebaseio.com/posts.json',this.blog).then(function(data){
              console.log(data);
          });
          this.submitted=true;
      }
  }
};
</script>

<style scoped>
#add-blog {
  margin: 5px 300px;
  overflow-wrap: break-word;
}
</style>
