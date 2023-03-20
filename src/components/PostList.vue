<template>
  <h1>Listado de posts consumiendo Placeholder-post API</h1>
  <ul class="post-list">
    <li 
        v-for="post in posts" 
        :key="post.id">
        <h2>{{ post.title }}</h2>
        <p> {{ post.body }}</p>
    </li>
  </ul>
</template>

<script lang="ts" setup>
    import PostService from '../services/PostService';
    import {onMounted, ref} from 'vue'

    const service = new PostService()
    const posts = service.getPosts()

    onMounted( async ()=>{
        await service.fetchAll()
    })


</script>

<style scoped>
  .post-list{
    width: auto;
    height: 75px;
    padding: 20px;
    list-style-type: none;
  }
  .post-list li {
    padding: 10px;
    width: 100%;
    border: 1px solid #ccc;
  }
  h1{
    color: rgb(96, 129, 238);
    font-size: 45px;
    margin: auto 5em;
    font-family: Arial, Helvetica, sans-serif;
  }
</style>
