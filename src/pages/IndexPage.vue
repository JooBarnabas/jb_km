<script setup lang="ts">
import CarCardComponent from "src/components/CarCardComponent.vue";
import CarCategorySelect from "src/components/CarCategorySelect.vue";
import { useStore } from "../stores/store";
import { onMounted } from "vue";
import { ref } from "vue";
import EditDialogComponent from "src/components/EditDialogComponent.vue";

const store = useStore();
// const selectedCategory = ref("Személyautó");
const cars = ref();


onMounted(() => {
  store.getAllCategories();
  store.one_GetAll();
});
  function updateCars(){
    cars.value = store.many.documents;
    console.log(cars.value)
  }
  updateCars();

  function editDocument(hirdetes) {
  store.many.document._id = hirdetes._id;
  store.app.showEditDialog = true;
  console.log(hirdetes._id);
}

  </script>
<template>
  <q-page>
    <div class="justify-center" style="min-height: 200px">
      <CarCategorySelect :updateCars = "updateCars"/>
    </div>

    <div class="row justify-center">
      <EditDialogComponent />
      <div v-for="(car, index) in cars" :key="car" class="col-12 col-md-6 col-lg-4">
        <CarCardComponent :car = "car" :index="index" @editDialog="editDocument(car)"/>
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
