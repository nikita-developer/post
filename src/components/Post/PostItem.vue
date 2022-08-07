<template>
    <div class="post-item">
        <div class="post-item__head">
            <MyButton class="post-item__button" @click="$emit('change', post)">Изменить</MyButton>
            <MyButton class="post-item__button" @click="$emit('remove', post)">Удалить</MyButton>
        </div>
        <div class="post-item__name">{{ post.title }}</div>
        <div class="post-item__description">{{ post.body }}</div>
    </div>
</template>

<script>
    export default {
        props: {
            post: {
                type: Object,
                require: true
            }
        }
    }
</script>

<style lang="scss" scoped>

    .post-item {
        border: 1px solid #d7d7d7;
        padding: 15px;
        display: flex;
        flex-direction: column;

        &__head {
            display: flex;
            justify-content: flex-end;
        }

        &__button {
            &:not(:last-child) {
                margin-right: 5px;
            }
        }

        &__name {
            margin-top: 5px;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px dashed #d7d7d7;
        }
    }
</style>