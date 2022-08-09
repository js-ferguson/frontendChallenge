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
      selectedCharacters: [],
      selectedTags: [],
    };
  },
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

    filteredCharacters(tag) {
      return [...new Set(this.selectedCharacters)];
    },
  },

  methods: {
    selectedChars(tag) {
      this.selectedTags.push(tag);
      this.selectedTags.forEach((tag) => {
        this.characterData.forEach((character) => {
          if (character.tags !== undefined) {
            character.tags.forEach((slot) => {
              if (slot.tag_name === tag) {
                this.selectedCharacters.push(character);
              }
            });
          }
        });
      });
    },
    calculateScore(index, attribute) {
      console.log("index:", index);
      let result = null;
      this.filteredCharacters[index].abilities.forEach((abil) => {
        if (abil.abilityName === attribute) {
          console.log(abil.abilityScore);
          result = abil.abilityScore;
        }
      });
      console.log(result);
      return result;
    },
    clearTags() {
      this.selectedCharacters = [];
      this.selectedTags = [];
    },
  },
});
</script>

<template>
  <div class="row">
    <div class="col-md-12 ms-auto me-auto">
      <span
        v-for="tag in tags"
        v-bind:key="tag"
        class="btn btn-outline-primary tag me-2 mt-2"
        :class="{ active: selectedTags.includes(tag) }"
        @click="selectedChars(tag)"
      >
        {{ tag }}
      </span>
      <div class="clear" @click="clearTags">Clear all</div>
    </div>
  </div>
  <div class="row justify-content-md-center mt-5">
    <div class="col-md-10">
      <table class="table">
        <thead>
          <tr>
            <th scope="col" class="col-md-3"><strong>Character</strong></th>
            <th scope="col" class="col-md-3"><strong>Tags</strong></th>
            <th scope="col"><strong>Power</strong></th>
            <th scope="col"><strong>Mobility</strong></th>
            <th scope="col"><strong>Technique</strong></th>
            <th scope="col"><strong>Survivability</strong></th>
            <th scope="col"><strong>Energy</strong></th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(char, index) in this.filteredCharacters.slice(0, 5)"
            v-bind:key="index"
          >
            <th scope="row">
              <input class="form-check-input mt-3" type="checkbox" value="" />
              <img class="thumbnail ms-5 me-5" :src="char.thumbnail" />
              <strong>{{ char.name }}</strong>
            </th>
            <td>
              <button
                v-for="tag in char.tags"
                v-bind:key="tag"
                class="btn btn-outline-primary tag me-2"
              >
                {{ tag.tag_name }}
              </button>
            </td>
            <td>
              {{ calculateScore(index, "Power") }}
            </td>
            <td>{{ calculateScore(index, "Mobility") }}</td>
            <td>{{ calculateScore(index, "Technique") }}</td>
            <td>{{ calculateScore(index, "Survivability") }}</td>
            <td>{{ calculateScore(index, "Energy") }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.thumbnail {
  border-radius: 50px;
  height: 50px;
  width: 50px;
  border: 1px solid #73acfe;
}

.tag {
  border-radius: 50px;
}

.clear {
  width: 100px;
  display: inline-block;
  transform: translate(5px, 8px);
}
</style>
