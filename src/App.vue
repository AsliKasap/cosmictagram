<script setup lang="ts">
import Layout from "./components/Layout.vue";
import Navbar from "./components/Navbar.vue";
import BottomBar from "./components/BottomBar.vue";
import { useRouter } from "vue-router";

const router = useRouter();

router.beforeEach(() => {
  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
});
</script>

<template>
  <div class="relative mx-auto">
    <Layout>
      <RouterView />
    </Layout>

    <!-- Absolute items -->
    <Navbar />
    <BottomBar />
  </div>
</template>

<style>
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.no-scrollbar::-webkit-scrollbar {
  width: 0;
  height: 0;
  background: transparent;
}
</style>