<template>
  <ul class="listStyle">
    <li
      class="listItemStyle"
      v-for="(list, index) in MenuList"
      v-motion
      :initial="{ opacity: 0, x: -1000 }"
      :enter="{
        opacity: 1,
        x: 0,
        transition: { type: 'spring', damping: 50, mass: 0.75 },
      }"
      :delay="(index + 1) * 200"
    >
      <span class="iconStyle">
        <span>
          <IconType :icon="list" />
        </span>
        <span>{{ list }}</span>
      </span>
    </li>
  </ul>
</template>

<script setup lang="ts">
const MenuList = [
  "Home",
  "Mail",
  "AboutUs",
  "Contact",
  "RateUs",
  "ChangePassword",
  "Settings",
];
</script>

<style>
.sideBarStyle {
  width: 100%;
  height: 100vh;
  background-color: #333;
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  padding: 1rem;
}

.listStyle {
  list-style: none;
  padding: 0;
  min-width: 200px;
}

.listItemStyle {
  margin-bottom: 1rem;
  font-size: 1.2rem;
  padding: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  border-radius: 5px;
}

.listItemStyle:hover {
  transform: scale(1.2);
}

.iconStyle {
  display: flex;
  color: #333;
  text-decoration: none;
  font-size: 14px;
  font-weight: 600;
  margin-left: 10px;
  line-height: 2;
}

.iconStyle span {
  display: flex;
  align-items: center;
}

.iconStyle span:first-child {
  margin-right: 1rem;
  width: 24px;
}
</style>
