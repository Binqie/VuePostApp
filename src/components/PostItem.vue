<template>
    <div class="post">
        <div>
            <div><strong>Title:</strong> {{post.title}}</div>
            <div><strong>Description:</strong> {{post.body}}</div>
        </div>
        <div class="post__btns">
            <my-button>Delete</my-button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
.post {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>