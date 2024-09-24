<template>
  <div class="bookCard" @click="handleClick()">
    <img :src="book.image" :alt="book.title" class="bookImageStyle" />
    <div class="bookContent">
      <h3 class="bookTittle">{{ book.title }}</h3>
      <p class="bookDescription">{{ book.description }}</p>
    </div>
  </div>
</template>

<script lang="ts" setup>
interface Book {
  id: number;
  author: string;
  title: string;
  image: string;
  description: string;
  content: string;
}

defineProps<{
  book: Book;
}>();

function handleClick() {}
</script>

<style scoped>
.bookCard {
  width: 100%;
  max-width: 250px;
  padding: 1rem;
  border-radius: 5px;
  background-color: #f8eadd;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.3s ease;
  margin-bottom: 1.5rem;
  margin-right: 1.6rem;
}

.bookImageStyle {
  width: 100%;
  aspect-ratio: 1;
  border-radius: 5px;
}

.bookContent {
  margin-top: 1rem;
}

.bookTittle {
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  color: #000;
}

.bookDescription {
  font-size: 0.8rem;
  color: #888;
}
</style>
