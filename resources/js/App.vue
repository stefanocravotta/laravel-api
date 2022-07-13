<template>
    <div class="container">
        <h1 class="text-center">Boolpress</h1>
        <h2 class="text-center">Lista post</h2>
        <ul>
            <li
            v-for="post in posts"
            :key="post.id"
            >
            <h3>{{post.title}}</h3>
            <p>{{post.content}}</p>

            </li>
        </ul>
    </div>
</template>

<script>
import Axios from 'axios'

    export default {
        name : 'App',
        data() {
            return {
                apiUrl : '/api/posts',
                posts : null
            }
        },
        methods: {
            getApi(){
                Axios.get(this.apiUrl)
                .then(r => {
                    //this.posts = r.data.posts.data
                    this.posts = r.data
                    console.log(this.posts);
                })
            }
        },
        mounted() {
            this.getApi()
        },
    }
</script>

<style lang="scss" scoped>

</style>
