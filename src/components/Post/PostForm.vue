<template>
    <div class="post-form">
        <h3 class="post-form__title">Добавить пост</h3>
        <p class="post-form__field-text">Имя</p>
        <MyInput class="post-form__field" v-model.trim="post.title"></MyInput>
        <p class="post-form__field-text">Описание</p>
        <MyTextarea class="post-form__field post-form__field--textarea" v-model.trim="post.body"></MyTextarea>
        <MyButton @click="createPost">Добавить</MyButton>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                post: {
                    title: '',
                    body: '',
                }
            }
        },
        methods: {
            createPost() {
                if (this.post.title && this.post.body) {
                    this.post.id = Date.now()
                    this.$emit('create', this.post)
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

    .post-form {
        &__field-text {
            margin-bottom: 5px;
            font-size: 14px;
            color: #747474;
        }

        &__field {
            margin-bottom: 15px;

            &--textarea {
                resize: vertical;
                max-height: 200px;
            }
        }

        &__title {
            margin-bottom: 15px;
        }
    }
</style>