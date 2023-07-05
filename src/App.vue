<script setup>
import { onMounted, ref } from "vue";
import AppHeader from "./components/AppHeader.vue";
import MatchPage from "./pages/MatchPage.vue";
import { Command } from "@tauri-apps/api/shell";

onMounted(async () => {
  const command = Command.sidecar("binaries/yoinker-backend");
  try {
    const output = await command.execute();
  } catch (err) {
    console.log("yoinker backend err: ", err);
  }
});

const currentView = ref("match");
</script>

<template>
  <div class="w-screen h-screen text-zinc-100 p-5 bg-zinc-800">
    <AppHeader />
    <!-- <MatchLoadouts /> -->
    <MatchPage v-if="currentView === 'match'" />
  </div>
</template>

<style scoped></style>
