<template>
  <q-layout view="lHh Lpr lFf" class="bg-accent">
    <NavBar />
    <div class="back-button q-mt-xl">
      <router-link
        :to="{
          path: '/',
        }"
      >
        <q-btn
          align="left"
          class="btn-fixed-width q-mt-lg q-mb-lg q-ml-xs"
          style="font-family: 'Tungsten'"
          color="accent"
          icon="arrow_back"
          ><span class="back-text q-ml-sm">BACK</span></q-btn
        >
      </router-link>
    </div>

    <div class="desktop-container text-white">
      <div class="desktop-agentInfos-container">
        <div class="mainInfo-text">
          <p class="role-title-desktop text-white">
            {{ agentData.role.displayName.toUpperCase() }}
          </p>
          <h1 style="font-family: 'Tungsten'">
            {{ agentData.displayName.toUpperCase() }}
          </h1>
          <hr class="name-line" />
          <p class="desc">{{ agentData.description }}</p>
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script setup lang="ts">
import { useRoute } from "vue-router";
import { ref } from "vue";
import gsap from "gsap";
import Search from "src/components/Search.vue";
import NavBar from "../pages/NavBar.vue";

const route = useRoute();
const agentData = ref(JSON.parse(route.query.data as string));

defineOptions({
  name: "AgentInfo",
});

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}

const abilitiesBG = ref<string[]>([
  "background-color: #FF4654;",
  "background-color: #757575;",
  "background-color: #757575;",
  "background-color: #757575;",
]);

const skillData = ref(agentData.value.abilities[0]);
const skillImgBg = ref("background-color: #1D1D1D");

//Ability Image
const abilityImage1 = ref();
const abilityImage2 = ref();
const abilityImage3 = ref();
const abilityImage4 = ref();

const toggleAbility = (num: number) => {
  skillImgBg.value = "background-color: #1D1D1D";
  abilitiesBG.value = abilitiesBG.value.map((_, index) =>
    index === num - 1
      ? "background-color: #FF4654;"
      : "background-color: #757575;"
  );
  skillData.value = agentData.value.abilities[num - 1];
  removeHover(num);
};

const hoverSkill = (num: number) => {
  if (abilitiesBG.value[num - 1] !== "background-color: #FF4654;") {
    switch (num) {
      case 1:
        gsap.to(abilityImage1.value, {
          duration: 0.2,
          scale: 1.2,
          ease: "power2.inOut",
        });
        break;
      case 2:
        gsap.to(abilityImage2.value, {
          duration: 0.2,
          scale: 1.2,
          ease: "power2.inOut",
        });
        break;
      case 3:
        gsap.to(abilityImage3.value, {
          duration: 0.2,
          scale: 1.2,
          ease: "power2.inOut",
        });
        break;
      case 4:
        gsap.to(abilityImage4.value, {
          duration: 0.2,
          scale: 1.2,
          ease: "power2.inOut",
        });
        break;
    }
  }
};

const removeHover = (num: number) => {
  switch (num) {
    case 1:
      gsap.to(abilityImage1.value, {
        duration: 0.2,
        scale: 1,
        ease: "power2.inOut",
      });
      break;
    case 2:
      gsap.to(abilityImage2.value, {
        duration: 0.2,
        scale: 1,
        ease: "power2.inOut",
      });
      break;
    case 3:
      gsap.to(abilityImage3.value, {
        duration: 0.2,
        scale: 1,
        ease: "power2.inOut",
      });
      break;
    case 4:
      gsap.to(abilityImage4.value, {
        duration: 0.2,
        scale: 1,
        ease: "power2.inOut",
      });
      break;
  }
};
</script>

<style scoped>
.desktop-agentInfos-container {
  width: 100%;
  background-image: url("../assets/Background/SideBG.png");
  background-repeat: no-repeat;
  padding: 0 50px;
}

.desktop-container {
  display: grid;
  grid-template-columns: 2fr 1fr;
  background-color: #01061e;
  color: white;
  padding: 0 5%;
  margin: auto auto 50px auto;
  background-image: url("../assets/Background/EffectsBG.png");
}
</style>
