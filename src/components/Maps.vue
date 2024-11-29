<template>
  <div class="bg-primary q-pa-lg all-maps-container" id="maps-section">
    <div class="main-map-container">
      <div class="row">
        <h1 class="text-title text-white" style="font-family: 'Tungsten'">
          MAPS
        </h1>
        <p class="text-white text-left map-desc" style="font-size: 16px">
          Each map is a playground to showcase your creative thinking.
          Purpose-built for team strategies, spectacular plays, and clutch
          moments. Make the play others will imitate for years to come
        </p>
      </div>

      <div v-for="map in data" :key="map.uuid" class="row maps-container">
        <div class="q-mb-lg map-container">
          <div class="flex justify-start row">
            <h1 class="map-title q-mb-xs q-mt-xs col-12 text-left">
              {{ map.displayName }}
            </h1>
            <p class="map-coordinates">{{ map.coordinates }}</p>
          </div>
          <div class="flex justify-center items-center">
            <img :src="map.splash" :alt="map.displayName" class="map-img" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Quasar } from "quasar";
import { defineComponent, ref, onMounted } from "vue";
import "quasar/src/css/index.sass";

const data = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch("https://valorant-api.com/v1/maps");
    const datas = await response.json();
    data.value = datas.data || [];
  } catch (error) {
    console.error(error);
  }
};

onMounted(() => {
  fetchData();
});
</script>

<style scoped>
.carousel-container {
  width: 100%;
  height: 200px;
}
.text-title,
.map-title {
  font-family: "Tungsten";
  color: white;
  letter-spacing: 1px;
}

.map-title {
  font-size: 60px;
}

.map-img {
  width: 100%;
}

.map-coordinates {
  font-size: 15px;
  color: white;
}
@media (min-width: 768px) {
  .all-maps-container {
    padding: 0 50px 0 50px !important;
  }
  .main-map-title {
    font-size: 100px;
    margin-bottom: 20px;
  }

  .main-map-desc {
    font-size: 30px;
    margin-bottom: 70px;
  }
  .map-title {
    font-size: 80px;
  }

  .map-coordinates {
    font-size: 20px;
    margin-bottom: 40px;
  }

  .map-container {
    margin-bottom: 100px;
  }
}

@media (min-width: 992px) {
  .all-maps {
    padding: 45px;
  }
}

@media (min-width: 1100px) {
  .all-maps-container {
    padding: 0 70px 0 70px !important;
  }
  .map-title {
    font-size: 90px;
  }

  .map-desc {
    margin-bottom: 100px;
  }

  .map-container {
    margin-bottom: 150px;
  }

  .map-coordinates {
    font-size: 24px;
  }
}
@media (min-width: 1250px) {
  .all-maps-container {
    padding: 0 40px 0 40px !important;
  }

  .main-map-container {
    width: 1200px;
    margin: auto;
  }

  .all-maps {
    width: 1200px;
    margin: auto;
    padding: 0;
  }
}
</style>
