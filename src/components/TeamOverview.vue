<script setup lang="ts">
defineProps<{
  characterData;
}>();
</script>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      count: 1,
    };
  },
  mounted() {},

  computed: {
    tags() {
      const arr: string[] = [];
      const tags = new Set<string>();
      this.characterData.forEach((element) => {
        arr.push(element.tags);
      });
      arr.flat().forEach((t) => {
        if (t !== undefined) {
          tags.add(t.tag_name);
        }
      });
      return tags;
    },

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
    <div class="col-md-12"></div>
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
