<script setup lang="ts">
import CarCardComponent from "src/components/CarCardComponent.vue";
import CarCategorySelect from "src/components/CarCategorySelect.vue";
import { useStore } from "../stores/store";
import { onMounted } from "vue";
// import { ref } from "vue";

const store = useStore();
// const selectedCategory = ref("Személyautó");



onMounted(() => {
  store.getAllCategories();
  store.one_GetAll();
  // store.other_GetAll(selectedCategory.value);
});

// function filterUpdate() {
//   if (!store.app.filter) {
//     store.app.filter = "";
//   }
//   if (store.app.filter.length > 0) {
//     store.many_Filter();
//   } else {
//     store.many_GetAll();
//   }
// }

</script>

<template>
  <q-page>
    <div class="justify-center" style="min-height: 200px">
      <q-field class="col-sm-3 col-md-4" label="Személyautó"></q-field>
      <CarCategorySelect />
    </div>

    <div class="row justify-center">
     
      <div v-for="car in 5" :key="car" class="col-12 col-md-6 col-lg-4">
        <CarCardComponent  />
      </div>
      <div class="bg-blue-5 col-sm-12 col-md-6 col-lg-4 col-xl-3"></div>
    </div>
  </q-page>
</template>

<style lang="scss" scoped>
h2 {
  font-size: 3vw;
}
</style>
