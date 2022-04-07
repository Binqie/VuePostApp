<template>
  <div class="navbar" >
      <div class="logo" @click="$router.push('/')">Vue 3</div>
      <div class="navbar__btns">
        <my-button @click="$router.push('/posts')">Posts</my-button>
        <my-button @click="$router.push('/about')">About</my-button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'my-navbar',
}
</script>

<style>
.navbar {
    display: flex;
    height: 50px;
    box-shadow: 2px 2px 4px gray;
    background-color: teal;
    align-items: center;
    padding: 10px 15px;
}
.navbar__btns {
    margin-left: auto;
}
</style>