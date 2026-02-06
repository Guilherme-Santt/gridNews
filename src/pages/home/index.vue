<script setup>
import axios from 'axios';
import { onMounted, ref, watch } from 'vue'
import Header from '../../components/header/index.vue'
import NewsGrid from '../../components/news/grid/index.vue'

onMounted(() => {
  const today = new Date();
  const year = today.getFullYear();
  const month = String(today.getMonth() + 1).padStart(2, '0');
  const day = String(today.getDate()).padStart(2, '0');
  const formattedDate = `${year}-${month}-${day}`;

  Response(formattedDate);
})

const Response = async (date) => {
  try {
    date = '2026-01-06';
    const keyApi = 'a7350cd58db34ab4943585443da4123e';

    const res = await axios.get(`https://newsapi.org/v2/everything?q=Apple&from=${date}&sortBy=popularity&apiKey=${keyApi}`);
    console.log('Resposta:', res.data);
    newsFromApi.value = res.data.articles;
    newsFromApiReply.value = structuredClone(res.data.articles);

  } catch (error) {
    console.error('Error fetching news:', error);
  }
} 

const newsFromApi = ref([]);
const newsFromApiReply = ref([]);
const searchQuery = ref('');

watch(() => searchQuery.value, (newQuery) => {
  console.log('Search query changed to:', newQuery);

  if (newQuery.trim() === '' || newQuery.length < 1) {
    newsFromApi.value = structuredClone(newsFromApiReply.value);
  } else {
    newsFromApi.value = newsFromApiReply.value.filter(article =>
      article.title.toLowerCase().includes(newQuery.toLowerCase()) ||
      (article.description && article.description.toLowerCase().includes(newQuery.toLowerCase()))
    );
  }
}, { deep: true });
</script>

<template>
  <Header
    @update:searchQuery="searchQuery = $event"
  />

  <NewsGrid :articles="newsFromApi" />
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
