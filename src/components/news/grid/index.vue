<template>
  <section class="news-grid">
    <NewsCard
      v-for="(item, index) in articles"
      :key="index"
      :news="item"
    />
  </section>
</template>

<script setup>
import NewsCard from '../card/index.vue'

defineProps({
  articles: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
.news-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
  padding: 32px;
}

.news-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
  padding: 32px;
}

/* Tablet */
@media (max-width: 1024px) {
  .news-grid {
    padding: 24px;
    gap: 20px;
  }
}

/* Mobile */
@media (max-width: 640px) {
  .news-grid {
    grid-template-columns: 1fr;
    padding: 16px;
  }
}

</style>
