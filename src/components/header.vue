<template>
<div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Blog</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
      <div class="navbar-nav">
          <router-link class="nav-link" aria-current="page" to="/">Show all blogs</router-link>
          <router-link  class="nav-link"  to="/add">Add a blog</router-link>
        <!-- <a class="nav-link" aria-current="page" href="/">Show all Blogs</a>
        <a class="nav-link" href="/add">Add a blog</a> -->
      </div>
    </div>
  </div>
</nav>
</div>

</template>

<script>

export default {
 
}
</script>

<style scoped>

</style>
