<script setup>
import {ref } from 'vue'
import ButtonVue from './components/ButtonVue.vue'
import Blogs from './components/Blogs.vue';
import PaginatePost from './components/PaginatePost.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';

const posts = ref([''])
const postXpage = 10;
const inicio = ref(0);
const fin = ref(postXpage)

const favorito = ref('')
const añadirFavorito = (title) => {
  favorito.value = title;
}
const loading = ref(true)
 
const next = () => {
  inicio.value = inicio.value + postXpage;
  fin.value = fin.value + postXpage;
}
const prev = () => {
  inicio.value = inicio.value - postXpage;
  fin.value = fin.value - postXpage;
}
fetch('https://jsonplaceholder.typicode.com/posts')
  .then((res) => res.json())
  .then((data) => posts.value = data)
  .finally ( ()=>{
    loading.value = false;
  })
</script>

<template>
  <LoadingSpinner v-if="loading"/>
  <div v-else class="container">

    <h1>APP</h1>
    
    <h2> Mi post favorito: {{ favorito }}</h2>
    <PaginatePost 
    @next = 'next' 
    @prev = 'prev' 
    :inicio='inicio' 
    :maxLength="posts.length"
    :fin='fin' 
    />
      
    <Blogs
    v-for="post in posts.slice(inicio, fin)"
    :title=post.title
    :id=post.id  
    :body=post.body
    @añadirFavorito ='añadirFavorito'/>

    <ButtonVue />
  
</div>
</template>