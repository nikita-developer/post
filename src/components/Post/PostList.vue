<template>
    <div class="post-list">
        <div v-if="posts.length" class="post-list__title">Список постов</div>
        <div v-else class="post-list__title">Постов нет</div>
        <PostItem
            class="post-list__item"
            v-for="post in posts"
            :key="post.id"
            :post="post"
            @remove="$emit('remove', post)"
            @change="$emit('change', post)"
        ></PostItem>
    </div>
</template>

<script>
    import PostItem from './PostItem.vue';
    export default {
        components: { PostItem },
        props: {
            posts: {
                type: Array,
                require: true
            }
        }
    }
</script>

<style lang="scss" scoped>
    .post-list {
        &__title {
            margin-bottom: 10px;
        }

        &__item {
            &:not(:last-child) {
                margin-bottom: 15px;
            }
        }
    }
</style>