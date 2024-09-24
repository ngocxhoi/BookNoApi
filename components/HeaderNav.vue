<template>
  <header>
    <div
      class="leftContainer"
      v-motion
      :initial="{ opacity: 0, x: -1000 }"
      :enter="{
        opacity: 1,
        x: 0,
        transition: { type: 'spring', damping: 30, mass: 0.99 },
      }"
    >
      <h1>Book App</h1>
      <input
        v-model="bookString"
        type="text"
        placeholder="Tell me what you like to read and we will get that..."
        v-motion
        :initial="{ opacity: 0, x: -2000 }"
        :enter="{
          opacity: 1,
          x: 0,
          transition: { type: 'spring', damping: 30, mass: 0.99 },
        }"
      />

      <div v-if="bookString" class="SearchContainer">
        <div
          @click="navigateTo(`/books/${book.id}`)"
          v-for="book in booksSearch"
          style="display: flex; gap: 1rem; margin-bottom: 10px"
        >
          <img :src="book.image" alt="" style="width: 50%" />
          <span style="font-size: 20px">{{ book.title }}</span>
        </div>
      </div>
    </div>

    <div
      class="rightContainer"
      v-motion
      :initial="{ opacity: 0, x: 1000 }"
      :enter="{
        opacity: 1,
        x: 0,
        transition: { type: 'spring', damping: 30, mass: 0.99 },
      }"
    >
      <NuxtLink to="/profile" class="avatarStyle">
        <img
          src="https://i.pravatar.cc/400"
          alt="avatar"
          v-motion="{
            initial: { opacity: 0, x: 100 },
            enter: {
              opacity: 1,
              x: 0,
              transition: { type: 'spring', damping: 30, mass: 0.99 },
            },
          }"
        />
      </NuxtLink>
    </div>
  </header>
</template>

<script setup lang="ts">
import { books } from "~/assets/constants/mockData";

const bookString = ref("");

const booksSearch = computed(() => {
  return books.filter((book) => {
    return book.title.toLowerCase().includes(bookString.value.toLowerCase());
  });
});
</script>

<style>
.SearchContainer {
  position: absolute;
  top: 80px;
  right: 0;
  width: 70%;
  border-radius: 5px;
  min-height: 100px;
  background-color: rgb(248, 234, 221);
  color: #000;
  z-index: 10000000;
}

header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 1rem 1rem 0;
  color: #fff;
  z-index: 10000000;
}

header .leftContainer {
  display: flex;
  align-items: center;
  position: relative;
}

header .leftContainer h1 {
  margin-right: 2rem;
  color: #000;
}

header .leftContainer input {
  padding: 0.7rem 1rem;
  margin-left: 3.6rem;
  border-radius: 70px;
  background-color: rgb(248, 234, 221);
  border: 2px solid #000;
  min-width: 320px;
}

header .rightContainer {
  display: flex;
  align-items: center;
}

header .rightContainer .avatarStyle {
  margin-right: 1rem;
}

header .rightContainer .avatarStyle img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
</style>
