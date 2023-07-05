<script setup>
import { ref, computed, reactive } from "vue";
import mockdata from "../mock/loadout";
import PlayerCard from "../components/match/PlayerCard.vue";
import PlayerList from "../components/match/PlayerList.vue";

const loadout = reactive(mockdata);
const players = computed(() => {
  const updatedArray = [];
  for (let key in loadout.Players) {
    if (loadout.Players.hasOwnProperty(key)) {
      const player = { ...loadout.Players[key] };
      player.id = key;
      updatedArray.push(player);
    }
  }
  return updatedArray;
});

//TODO: maybe sort into teams. Super easy: filter by player.Team Blue/Red
</script>

<template>
  <div class="bg-zinc-700 justify-between p-5 w-full flex gap-10">
    <div class="w-1/2" v-if="players">
      <PlayerCard v-for="player in players" :key="player.id" :player="player" />
    </div>
    <div class="w-1/2">
      <!-- <PlayerList /> -->
      <pre class="w-1/2 whitespace-pre">
        <code>
            <!-- {{ loadout.Players }} -->
          {{ players[0] }}
        </code>
      </pre>
    </div>
  </div>
</template>
