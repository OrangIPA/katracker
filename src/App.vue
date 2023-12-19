<script setup lang="ts">
import { computed, ref } from "vue";
import LoginPage from "./views/LoginPage.vue";
import Status from './views/Status.vue'
import NotFound from "./views/NotFound.vue";

const routes: any = {
  "/": Status,
  "/login": LoginPage
};

const currentPath = ref(window.location.hash);

window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"] || NotFound;
});
</script>

<template>
  <a href="#/">status</a>
  <a href="#/login">LoginPage</a>
  <component :is="currentView" />
</template>

<style scoped></style>
