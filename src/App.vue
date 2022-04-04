<template>
    <div class="app">
        <post-form @create="createPost"/>
        <post-list :posts="posts"/>
    </div>
</template>

<script>
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue'
export default {
    components: {
        PostForm, 
        PostList
    },
    data() {
        return {
            posts: [
                {id: 1, title: 'Js', body: 'Js is a programming language.'},
                {id: 2, title: 'Vue', body: 'Vue is a JS framework.'},
                {id: 3, title: 'React', body: 'React is a JS framework.'},
            ],     
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post);
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    border: 0;
    box-sizing: border-box;
}

.app {
    margin: 20px;
}
</style>