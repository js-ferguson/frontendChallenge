<script setup lang="ts">
defineProps<{
  characterData;
}>();
</script>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  computed: {
    attributeAverages() {
      return {
        Power: "-",
        Mobility: "-",
        Technique: "-",
        Survivability: "-",
        Energy: "-",
      };
    },
  },

  methods: {
    click(tag) {
      console.log(tag);
    },
  },
});
</script>

<template>
  <h3 class="col-md-12 mt-4 text-center">
    Select your squad to defend Earthrealm
  </h3>
  <div class="row">
    <div class="col-md-1"></div>
  </div>
  <div class="row justify-content-md-center">
    <div
      v-for="(value, key, index) in attributeAverages"
      v-bind:key="index"
      class="col-md-1 text-center"
    >
      {{ key }}
    </div>
  </div>
  <div class="row justify-content-md-center">
    <div
      v-for="(value, key, index) in attributeAverages"
      v-bind:key="index"
      class="col-md-1 text-center"
    >
      {{ value }}
    </div>
  </div>
</template>

<style scoped>

</style>
