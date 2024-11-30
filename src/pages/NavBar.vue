<template>
  <div>
    <q-header class="bg-dark">
      <q-toolbar>
        <!-- <q-btn
          flat
          dense
          round
          aria-label="Menu"
          @click="toggleLeftDrawer"
          class="q-mr-md"
          style="margin-bottom: 7px"
          v-if="screenWidth < 1100"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <line x1="3" y1="12" x2="21" y2="12"></line>
            <line x1="3" y1="6" x2="21" y2="6"></line>
            <line x1="3" y1="18" x2="21" y2="18"></line>
          </svg>
        </q-btn> -->

        <a href="https://www.riotgames.com/en" target="_blank">
          <img
            v-if="screenWidth < 1100"
            src="../assets/Logo/riotLogo.png"
            class="riot-logo"
          />
          <img
            v-else
            src="../assets/Logo/riotLogo.png"
            class="riot-logo q-ml-xl"
          />
        </a>
        <a href="https://playvalorant.com/en-sg/" target="_blank">
          <img
            v-if="screenWidth < 1100"
            src="../assets/Logo/valorantLogo.png"
            class="valo-logo"
          />
          <img
            v-else
            src="../assets/Logo/valorantLogo.png"
            class="valo-logo q-ml-sm"
          />
        </a>
      </q-toolbar>
    </q-header>
    <!-- 
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      class="bg-secondary text-white"
      v-if="screenWidth < 1100"
    >
      <q-scroll-area class="fit">
        <img
          v-if="screenWidth < 1100"
          src="../assets/Logo/valorantLogo.png"
          class="valo-logo"
        />
        <q-list>
          <div v-for="(menuItem, index) in menuList" :key="index">
            <q-item
              clickable
              :active="menuItem.label === 'Outbox'"
              v-ripple
              @click="drawerToggle(menuItem.label)"
            >
              <q-item-section
                style="font-family: 'Tungsten; font-size: 30px; letter-spacing: 1px;"
              >
                {{ menuItem.label }}
              </q-item-section>
            </q-item>
            <q-separator :key="'sep' + index" v-if="menuItem.separator" />
          </div>
        </q-list>
      </q-scroll-area>
    </q-drawer> -->
  </div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import { matMenu } from "@quasar/extras/material-icons";
import { mdiAbTesting } from "@quasar/extras/mdi-v6";
import { fasFont } from "@quasar/extras/fontawesome-v5";
const menuList = [
  {
    label: "AGENTS",
    separator: true,
  },
  {
    label: "MAPS",
    separator: false,
  },
];

const drawer = ref(false);

defineOptions({
  name: "NavBar",
});

const screenWidth = ref(window.innerWidth);

const updateWidth = () => {
  screenWidth.value = window.innerWidth;
};

onMounted(() => {
  window.addEventListener("resize", updateWidth);
});

onUnmounted(() => {
  window.removeEventListener("resize", updateWidth);
});

const drawerToggle = (label: string): void => {
  // Convert label to section ID
  const sectionId = label.toLowerCase().replace(" ", "-"); // e.g., "AGENTS" -> "agents"
  const sectionElement = document.getElementById(`${sectionId}-section`);

  // Toggle drawer (close it)
  toggleLeftDrawer();

  console.log("SECTION ID:", sectionId);
  console.log("SECTION ELEMENT:", sectionElement);

  if (sectionElement) {
    // Scroll to the section
    sectionElement.scrollIntoView({
      behavior: "smooth",
      block: "start",
    });

    // Log position for debugging
    const rect = sectionElement.getBoundingClientRect();
    console.log(`Position - Top: ${rect.top}, Left: ${rect.left}`);
  } else {
    console.warn(`Section for label "${label}" not found.`);
  }
};

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
