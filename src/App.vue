<template>
    <div class="post">
        <h1 class="post__title">Страница с постами</h1>
        <MyModal :visible="modalVisible" @hide="hideModal">
            <PostForm class="post__form" @create="createPost"></PostForm>
        </MyModal>

        <MyModal :visible="modalVisible" @hide="hideModal">
            <PostChange></PostChange>
        </MyModal>

        <MyButton class="post__button" @click="openModal">Добавить пост</MyButton>
        <PostList v-if="!isPostsLoading" :posts="posts" @remove="removePost" @change="changePost"></PostList>
        <div v-else>Идет загрузка...</div>
    </div>
</template>

<script>
    import PostForm from './components/Post/PostForm.vue';
    import PostList from './components/Post/PostList.vue';
    import axios from 'axios';
    import PostChange from './components/Post/PostChange.vue';
    export default {
        components: { PostForm, PostList, PostChange },
        data() {
            return {
                posts: [],
                modalVisible: false,
                isPostsLoading: false,
            }
        },
        methods: {
            createPost(post) {
                this.posts.push(post)
                this.hideModal()
            },
            removePost(post) {
                this.posts = this.posts.filter(p => p.id !== post.id)
            },
            changePost(post) {
                this.posts.forEach((element) => {
                    this.openModal()
                    if (element.id === post.id) {
                        element.name = '1234'
                    }
                })
            },
            openModal() {
                this.modalVisible = true
            },
            hideModal() {
                this.modalVisible = false
            },
            async fetchPosts () {
                try {
                    this.isPostsLoading = true
                    setTimeout( async () => {
                        const response = await axios.get('https://jsonplaceholder.typicode.com/posts')
                        this.posts = response.data
                        this.isPostsLoading = false
                    }, 1000)
                } catch (e) {
                    alert('Ошибка')
                }
            }
        },
        mounted() {
            this.fetchPosts()
        }
    }
</script>

<style lang="scss">


    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .post {
        padding: 15px;

        &__title {
            margin-bottom: 15px;
        }

        &__add-post {
            margin-bottom: 15px;
        }

        &__button {
            margin-bottom: 15px;
        }
    }
</style>