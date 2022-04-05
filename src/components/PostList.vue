<template>
    <div v-if="posts.length > 0">
        <h3>Posts list: </h3>
        <post-item 
            v-for="post of posts"
            @remove="$emit('remove', post)" 
            :post="post"
            :key="post.id"/>
    </div>
    <h2 style="color: red" v-else>There are no posts!</h2>
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
