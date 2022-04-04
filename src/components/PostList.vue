<template>
    <div>
        <h3>Posts list: </h3>
        <post-item 
            v-for="post of posts" 
            :post="post"
            :key="post.id"/>
    </div>
</template>

<script>
import PostItem from './PostItem.vue'

export default {
  components: { PostItem },
    props: {
        posts: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.post {
    border: 2px solid teal;
    margin-bottom: 15px;
    padding: 10px;
}
</style>
