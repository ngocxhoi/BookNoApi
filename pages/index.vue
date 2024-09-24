<template>
  <HeaderNav />

  <div class="containerStyle">
    <section class="content-left">
      <SideBar />
    </section>

    <div class="content-right">
      <h1>ALL BOOKS</h1>
      <ul>
        <li
          v-for="(book, index) in books"
          v-motion
          :initial="{ opacity: 0, x: 200 * (index + 1) }"
          :enter="{
            opacity: 1,
            x: 0,
            transition: { type: 'spring', damping: 50, mass: 0.75 },
          }"
        >
          <NuxtLink :to="`/books/${book.id}`">
            <BookCard :book="book" />
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { books } from "~/assets/constants/mockData";
</script>

<style scoped>
.containerStyle {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  z-index: 100;
}

.content-left {
  width: 30%;
  z-index: 10;
}

.content-right {
  width: 68%;
  background-color: #f8eadd;
  margin: 0 30px;
  padding: 10px 1px;
  border-radius: 20px;
  box-sizing: border-box;
  padding-left: 30px;
}

.content-right ul {
  list-style: none;
  margin: 0;
  padding: 0;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
