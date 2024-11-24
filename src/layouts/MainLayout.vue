<template>
  <q-layout view="lHh Lpr lFf" class="bg-accent">
    <NavBar />
    <q-page-container>
      <search />
    </q-page-container>

    <q-page-container class="q-pa-lg">
      <AllAgents />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Search from "src/components/Search.vue";
import AllAgents from "src/components/AllAgents.vue";
import NavBar from "../pages/NavBar.vue";

defineOptions({
  name: "MainLayout",
});

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style scoped>
.riot-logo {
  width: 60px;
}
.valo-logo {
  width: 60px;
}
</style>
