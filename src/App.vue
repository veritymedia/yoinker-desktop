<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { onMounted } from "vue";
import MatchLoadouts from "./pages/MatchLoadouts.vue";
import { Command } from "@tauri-apps/api/shell";

onMounted(async () => {
  const command = Command.sidecar("binaries/yoinker-backend");
  try {
    const output = await command.execute();
  } catch (err) {
    console.log("yoinker backend err: ", err);
  }
});
</script>

<template>
  <div class="container bg-blue-500">
    <MatchLoadouts />
  </div>
</template>

<style scoped></style>
