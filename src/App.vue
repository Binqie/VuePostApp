<template>
    <div class="app">
        <h1>Posts page</h1>
        <div class="app__btns">
            <my-button @click="showDialog">Create new post</my-button>
            <my-select v-model="selectedSort" :options="sortOptions"></my-select>
        </div>
        <my-dialog v-model:show="dialogVisible">
            <post-form @create="createPost"/>
        </my-dialog>
        <post-list :posts="posts"
                    @remove="removePost"
                    v-if="!isPostsLoading"/>
        <div v-else>Posts are loading...</div>
    </div>
</template>

<script>
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue'
import MyButton from './components/UI/MyButton.vue'
import MyDialog from './components/UI/MyDialog.vue'
import axios from 'axios'
import MySelect from './components/UI/MySelect.vue'

export default {
    components: {
        PostForm, 
        PostList,
        MyDialog,
        MyButton,
        MySelect
    },
    data() {
        return {
            posts: [], 
            modificatorValue: '',
            selectedSort: '',
            sortOptions: [
                {value: 'title', name: 'Sort by title'},
                {value: 'body', name: 'Sort by body'},
            ],
            dialogVisible: false,
            isPostsLoading: false   
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
        },
        showDialog() {
            this.dialogVisible = true;
        },
        async fetchPosts() {
            try {
                this.isPostsLoading = true;
                setTimeout(async () => {
                    await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10').then(response => {
                        this.posts = response.data;
                        this.isPostsLoading = false;
                    }); 
                }, 1000)
            } catch (error) {
                alert(error);
            }
        }
    },
    mounted() {
        this.fetchPosts()
    },
    watch: {
        selectedSort(newValue) {
            console.log(newValue)
        },
        dialogVisible(newValue) {
            console.log(newValue)
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
.app__btns {
    margin: 20px 0;
    display: flex;
    justify-content: space-between;
}
</style>