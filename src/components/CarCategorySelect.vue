<script setup lang="ts">
import { ref } from "vue";
import { useStore } from "src/stores/store";
const store = useStore();
const p = defineProps(["updateCars"]);
const selectedCategory = ref("Személyautó");

const categories = ref();

store
  .one_GetAll()
  .then((res) => console.log(res))
  .catch((err) => {
    console.error(err);
  });
async function call() {
  store.one_getByCategory(selectedCategory.value);
  await new Promise((res) => setTimeout(res, 200));
  p.updateCars();
}
const selectionChanged = () => {
  call();
};

categories.value = store.other.documents;
store.one_getByCategory(selectedCategory.value);
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
      :options="categories"
      @update:model-value="selectionChanged()"
    ></q-select>
  </div>
</template>

<style scoped>
.categories {
  width: 100%;
}
</style>
