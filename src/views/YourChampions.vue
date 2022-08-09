<script setup lang="ts">
defineProps<{
  characterData;
}>();
</script>

<script lang="ts">
import { defineComponent } from "vue";
import TeamOverview from "../components/TeamOverview.vue";
import ChampionSelect from "../components/ChampionSelect.vue";
import SearchBar from "../components/SearchBar.vue";

export default defineComponent({});
</script>

<template>
  <div class="row text-center">
    <nav></nav>
    <div class="col-md-12">
      <header>
        <img
          alt="Kombat logo"
          class="logo"
          src="@/assets/Mortal-Kombat-Logo.png"
          width="200"
          height="110"
        />
      </header>
    </div>
  </div>
  <TeamOverview :characterData="characterData" />
  <SearchBar :characterData="characterData" />
  <ChampionSelect :characterData="characterData" />
</template>

<style scoped>
nav {
  background-color: black;
  height: 80px;
  margin-bottom: -55px;
}
</style>
