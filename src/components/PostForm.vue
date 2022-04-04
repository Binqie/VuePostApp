<template>
    <form @submit.prevent>
        <h4>Add new post</h4>
        <my-input 
            v-model="post.title"
            @input="post.title = $event.target.value"
            type="text" 
            name="" 
            placeholder="Title"
            />
        <my-input 
            v-model="post.body"
            @input="post.body = $event.target.value"
            type="text" 
            name="" 
            placeholder="Description"
            />
        <my-button  
            @click="createPost"
            >Add</my-button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
        createPost() {
            this.$emit('create', {id: Date.now(), title: this.post.title, body: this.post.body});
            this.post.title = '';
            this.post.body = '';
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
    flex-direction: column;
}
</style>