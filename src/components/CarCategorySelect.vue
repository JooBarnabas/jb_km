<script setup lang="ts">
import { ref } from "vue";
import { useStore } from "src/stores/store";
const store = useStore();

const selectedCategory = ref("Személyautó");

store.one_GetAll()
    .then((res) =>
    console.log(res))
    .catch((err) => {
      console.error(err);
    });   

const selectionChanged = () => {
  store.other_GetAll(selectedCategory.value);
};
</script>

<template>
  <div class="q-pa-md categories row justify-center">
    <q-select
      v-model="selectedCategory"
      emit-value
      label="Kategória"
      map-options
      option-label="nev"
      option-value="nev"
      :options="store.many.documents"
      @update:model-value="selectionChanged()"
    ></q-select>
  </div>

  {{ selectedCategory }}
</template>

<style scoped>
.categories {
  width: 100%;
}
</style>
