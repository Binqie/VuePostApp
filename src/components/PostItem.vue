<template>
    <div class="post">
        <div>
            <div>{{post.id}}</div>
            <div><strong>Title:</strong> {{post.title}}</div>
            <div><strong>Description:</strong> {{post.body}}</div>
        </div>
        <div class="post__btns">
            <my-button
                @click="$router.push(`/posts/${post.id}`)"
                >Open</my-button>
            <my-button
                style="margin-left: 5px"
                @click="$emit('remove', post)"
                >Delete</my-button>
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
.post__btns {
    display: flex;
    justify-content: flex-end;
}
</style>