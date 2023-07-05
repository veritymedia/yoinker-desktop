<script setup>
const props = defineProps({
  player: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div class="flex flex-col gap-10 w-full">
    <div class="w-full flex items-center justify-between">
      <div class="flex relative">
        <p
          class="absolute -bottom-4 font-bold opacity-70 left-1/2 -translate-x-1/2 text-3xl"
        >
          {{ player.Name }}
        </p>
        <img
          :src="player.Agent"
          :alt="player.Name"
          class="w-16 h-16 rounded-full ring-2 ring-zinc-200"
        />
      </div>
      <div class="flex flex-col gap-1">
        <p class="uppercase text-sm font-bold">sprays</p>
        <div class="flex gap-4">
          <div v-for="spray in player.Sprays" :key="spray.displayName">
            <img :src="spray.displayIcon" alt="" class="w-10" />
          </div>
        </div>
      </div>
      <div class="text-xl items-end flex-col flex">
        <p>AlvarezTico</p>
        <div
          class="flex items-center gap-2 text-xs uppercase font-bold text-zinc-400"
        >
          <p class="">
            {{ player.Title }}
          </p>
          <div class="">
            Level <span class="text-zinc-100">{{ player.Level }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="grid grid-cols-5 text-zinc-400">
      <div class="" v-for="weapon in player.Weapons" :key="weapon.weapon">
        {{ weapon.skinDisplayName }}
        <img :src="weapon.skinDisplayIcon" alt="" class="w-40" />
      </div>
    </div>
  </div>
</template>
