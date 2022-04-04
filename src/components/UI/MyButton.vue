<template>
  <button class="btn">
      <slot></slot>
  </button>
</template>

<script>
export default {
    name: 'my-button'
}
</script>

<style scoped>
.btn {
    align-self: flex-end;
    border: 1px solid teal;
    padding: 10px 20px;
    margin: 5px 0;
}
</style>