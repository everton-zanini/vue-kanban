<template>
  <div id="app">
    <div class="container grid-lg">
      <header class="navbar">
        <section class="navbar-section">
          <router-link to="/" class="btn btn-link">Home</router-link>
          <router-link to="/kanban" class="btn btn-link">Kanban</router-link>
        </section>
        <section class="navbar-center">
          <img class="img-responsive image-logo" src="@/assets/logo.png" alt="todo kanban">
        </section>
        <section class="navbar-section">
          <a href="" class="btn btn-link">Linkedin</a>
          <a href="" class="btn btn-link">Github</a>
        </section>
      </header>
      <router-view/>
    </div>
    
  </div>
</template>

<script>
export default{}
</script>

<style scoped>
.image-logo {
  max-width: 80px;
}
</style>

