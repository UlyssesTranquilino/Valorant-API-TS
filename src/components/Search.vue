<template>
  <div
    class="search-container q-pt-xl q-pb-lg flex items-center justify-center row text-white"
  >
    <div class="col-12 items-center justify-center">
      <p class="q-ma-xs col-12 text-center p-text">
        A 5v5 character-based tactical shooter
      </p>
      <h1 class="valo-title q-ma-xs col-12 text-center">VALORANT</h1>
    </div>
    <div class="q-pa-xs q-ma-xs search flex items-center justify-center row">
      <q-input
        filled
        v-model="text"
        :dense="dense"
        class="bg-white q-mt-xs input-search"
      >
        <template v-slot:prepend>
          <q-icon name="search"></q-icon>
        </template>
      </q-input>
      <div class="search-button-container q-mt-lg">
        <q-btn
          square
          style="color: white"
          label="SEARCH AGENT"
          class="bg-primary searh-button q-ma-xs"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const dense = ref<string>("dense");
const text = ref<string>("");
</script>

<style scoped>
@import url("https://fonts.cdnfonts.com/css/valorant");

.search-container {
  background-image: url("../assets/Background/SearchBg.png");
  background-size: cover;
  height: 400px;
  background-position: center;
}

.search {
  width: 250px;
  height: 35px;
  transform: translateY(-90px);
}

.valo-title {
  font-family: "Valorant";
  font-size: 50px;
}

.search-button-container {
  border: 1px solid white;
}

@media (min-width: 1100px) {
  .search {
    width: 450px;
    height: 95px;
    transform: translateY(-90px);
  }

  .p-text {
    font-size: 15px;
  }
  .input-search {
    width: 900px;
  }

  .valo-title {
    font-size: 70px;
    margin: 0;
    transform: translateY(10px);
  }

  .search-container {
    height: 500px;
  }
}
</style>
