<template>
  <q-layout view="lHh Lpr lFf" class="bg-accent">
    <q-header class="bg-dark">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
          class="q-mr-md"
        />
        <img src="../assets/Logo/riotLogo.png" class="riot-logo" />
        <img src="../assets/Logo/valorantLogo.png" class="valo-logo" />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      class="bg-secondary text-white"
    >
    </q-drawer>

    <q-page-container>
      <search />
    </q-page-container>

    <q-page-container class="q-pa-lg">
      <AllAgents />
    </q-page-container>
    <!-- 
    <q-page-container>
      <router-view />
    </q-page-container> -->
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Search from "src/components/Search.vue";
import AllAgents from "src/components/AllAgents.vue";

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
