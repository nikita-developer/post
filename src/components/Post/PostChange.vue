<template>
    <div class="post-change">
        <h3 class="post-change__title">Изменить пост</h3>
        <p class="post-change__field-text">Новое имя</p>
        <MyInput class="post-change__field" v-model.trim="post.title"></MyInput>
        <p class="post-change__field-text">Новое описание</p>
        <MyTextarea class="post-change__field" v-model.trim="post.body"></MyTextarea>
        <MyButton @click="createPost">Изменить</MyButton>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                post: {
                    title: 'dfs',
                    body: '',
                }
            }
        },
        methods: {
            changePost() {
                if (this.post.title && this.post.body) {
                    this.post.id = Date.now()
                    this.$emit('changePostData', this.title, this.body)
                    this.post = {
                        title: '',
                        body: ''
                    }
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>