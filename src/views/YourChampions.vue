<script setup lang="ts">
defineProps<{
  // msg: string;
  characterData;
}>();
</script>

<script lang="ts">
import { defineComponent } from "vue";
import TeamOverview from "../components/TeamOverview.vue";
import ChampionSelect from "../components/ChampionSelect.vue";
import SearchBar from "../components/SearchBar.vue";

export default defineComponent({
  data() {
    return {
      count: 1,
    };
  },
  // mounted() {},

  // computed: {
  //   tags() {
  //     const arr: string[] = [];
  //     const tags = new Set<string>();
  //     this.characterData.forEach((element) => {
  //       arr.push(element.tags);
  //     });
  //     arr.flat().forEach((t) => {
  //       if (t !== undefined) {
  //         tags.add(t.tag_name);
  //       }
  //     });
  //     return tags;
  //   },
  // },

  methods: {
    // click(tag) {
    //   console.log(tag);
    // },
  },
});
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

        <!-- <div class="wrapper">
      <YourChampions msg="Your Champions!" :characterData="json" /> -->

        <!-- <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav> -->
        <!-- </div> -->
      </header>
    </div>

    <!-- <div class="wrapper row"> -->
    <!-- <ChampionSelect msg="Your Champions!" :characterData="json" /> -->

    <!-- <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/about">About</RouterLink>
        </nav> -->
    <!-- </div> -->
  </div>
  <TeamOverview :characterData="characterData" />
  <SearchBar :characterData="characterData" />
  <ChampionSelect :characterData="characterData" />
  <!-- <RouterView /> -->
</template>

<style scoped>
nav {
  background-color: black;
  height: 80px;
  margin-bottom: -55px;
}

/* h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.tag {
  border-radius: 50px;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
} */
</style>
