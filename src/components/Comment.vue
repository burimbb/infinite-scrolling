<template>
    <div class="comment">
        <h1 v-text="name"></h1>
        <p v-text="body"></p>
    </div>
</template>
<script>
export default {
    name: 'comment',
    props: {
        postId: Number,
        id: Number,
        name: String,
        email: String,
        body: String,
    },
    data(){
        return {

        }
    }
}
</script>