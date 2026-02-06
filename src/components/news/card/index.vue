<template>
    <article class="card">
      <img
        v-if="news.urlToImage"
        :src="news.urlToImage"
        :alt="news.title"
        class="image"
      />
  
      <div class="content">
        <span class="source">{{ news.source?.name }}</span>
  
        <h2 class="title">{{ news.title }}</h2>
  
        <p class="description">
          {{ news.description }}
        </p>
  
        <div class="footer">
          <span class="author">
            {{ news.author || 'Autor desconhecido' }}
          </span>
  
          <span class="date">
            {{ formattedDate }}
          </span>
        </div>
  
        <a
          :href="news.url"
          target="_blank"
          rel="noopener"
          class="read-more"
        >
          Ler matéria →
        </a>
      </div>
    </article>
  </template>
  
  <script setup>
  import { computed } from 'vue'
  
  const props = defineProps({
    news: {
      type: Object,
      required: true
    }
  })
  
  const formattedDate = computed(() =>
    new Date(props.news.publishedAt).toLocaleDateString('pt-BR', {
      day: '2-digit',
      month: 'short',
      year: 'numeric'
    })
  )
  </script>
  
  <style scoped>
  .card {
    background: white;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    display: flex;
    flex-direction: column;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
  }
  
  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 18px 45px rgba(0,0,0,0.12);
  }
  
  .image {
    width: 100%;
    height: 190px;
    object-fit: cover;
  }
  
  .content {
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .source {
    font-size: 0.75rem;
    font-weight: 600;
    color: #3b82f6;
    text-transform: uppercase;
  }
  
  .title {
    font-size: 1.05rem;
    font-weight: 700;
    color: #111;
    line-height: 1.3;
  }
  
  .description {
    font-size: 0.9rem;
    color: #555;
    line-height: 1.4;
  }
  
  .footer {
    display: flex;
    justify-content: space-between;
    font-size: 0.75rem;
    color: #777;
    margin-top: 6px;
  }
  
  .read-more {
    margin-top: 8px;
    font-weight: 600;
    color: #3b82f6;
    text-decoration: none;
    align-self: flex-start;
  }

  .image {
  width: 100%;
  height: 190px;
  object-fit: cover;
}

/* Mobile */
@media (max-width: 640px) {
  .image {
    height: 160px;
  }

  .title {
    font-size: 1rem;
  }

  .description {
    font-size: 0.85rem;
  }
}

</style>
