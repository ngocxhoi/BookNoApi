<template>
  <div
    v-motion
    :initial="{ opacity: 0, x: 1000 }"
    :enter="{
      opacity: 1,
      x: 0,
      transition: { type: 'spring', damping: 44, mass: 0.75 },
    }"
  >
    <section
      class="appBar"
      v-motion
      :initial="{ opacity: 0, y: -1000 }"
      :enter="{
        opacity: 1,
        y: 0,
        transition: { type: 'spring', damping: 44, mass: 0.75 },
      }"
    >
      <div @click="navigateTo('/')" class="leftIcons" style="width: 24px">
        <IconType
          icon="chevron-left"
          style="font-size: 20px; cursor: pointer"
        />
      </div>

      <div class="readTitle">
        <h2 class="titleStyles">{{ book?.title }}</h2>
      </div>

      <div class="readIcons">
        <button class="saveButton">Save</button>
        <div>
          <IconType icon="Settings" />
        </div>
        <div>
          <IconType icon="Share" />
        </div>
        <div>
          <IconType icon="Search" />
        </div>
      </div>
    </section>

    <main class="bookContainer" v-html="bookTitle"></main>
  </div>
</template>

<script setup lang="ts">
import { books } from "~/assets/constants/mockData";

const route = useRoute();

const book = computed(() =>
  books.find((book) => book.id === Number(route.params.id))
);

const bookTitle = computed(
  () =>
    `<aside><h1 class='center'>${book.value?.title}</h1> <span class='center small'>By ${book.value?.author}</span>` +
    book.value?.content
);
</script>

<style>
.appBar {
  display: flex;
  width: 90%;
  margin: auto;
  justify-content: space-between;
  align-items: center;
  min-height: 5vh;
  margin-top: 10px;
  margin-bottom: 10px;
}

.saveButton {
  padding: 10px 30px;
  background: transparent;
  border-radius: 30px;
  border: 1px solid #000;
  margin-right: 20px;
  cursor: pointer;
}

.saveButton:hover {
  background: #000;
  color: #fff;
}

.titleStyles {
  text-align: center;
  text-transform: uppercase;
  padding-left: 100px;
}

.readTitle {
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  color: #000;
}

.readIcons {
  display: flex;
  align-items: center;
  gap: 1rem;
  height: 100%;
  color: #333;
  text-decoration: none;
  font-size: 14px;
  font-weight: 600;
  margin-left: 10px;
  line-height: 2;
}

.readIcons div {
  width: 24px;
  display: flex;
  align-items: center;
}

.bookContainer {
  height: 80vh;
  width: 95%;
  margin: auto;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.bookContainer aside {
  width: 42.5%;
  background: #f8eadd;
  border-radius: 20px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  padding: 20px 30px;
  flex-grow: 1;
  margin: 20px 10px;
}

.bookContainer aside p {
  line-height: 21px;
  font-size: 20px;
}

.center {
  text-align: center;
  font-size: 36px;
  font-weight: 300;
  margin-bottom: 4px;
}

.small {
  font-size: 16px;
  text-align: center;
  display: block;
  margin-bottom: 40px;
}
</style>
