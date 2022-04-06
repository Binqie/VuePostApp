<template>
    <div v-if="posts.length > 0">
        <h3>Posts list: </h3>
        <transition-group name="posts-list">
            <post-item 
            v-for="post of posts"
            @remove="$emit('remove', post)" 
            :post="post"
            :key="post.id"/>
        </transition-group>
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
.posts-list-item {
  display: inline-block;
  margin-right: 10px;
}
.posts-list-enter-active,
.posts-list-leave-active {
  transition: all 0.3s ease;
}
.posts-list-enter-from,
.posts-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.posts-list-move {
    transition: transform 0.5s ease;
}
</style>