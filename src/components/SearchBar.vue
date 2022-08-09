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

  computed: {},

  methods: {
    click(tag) {
      console.log(tag);
    },
  },
});
</script>

<template>
  <h3 class="col-md-12 mt-4 mb-4 text-center">Search</h3>
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
