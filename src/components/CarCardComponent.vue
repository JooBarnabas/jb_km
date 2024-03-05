<template>
    <div class="main">
        <h5 class="bg-darkBegie">Cím</h5>

        <ul class="bg-lightBegie">
            <li>Szín: {{ }}</li>
            <li>Évjárat: {{ }}</li>
            <li>Hengerűrtartalom: {{ }}</li>
            <li>Hirdetés dátuma: {{ }}</li>
        </ul>

        <div class="bg-darkBegie">
            <p>szöveg</p>
            <hr>
            <q-toggle v-model="toggleValue" />
        </div>

        <div class="bg-lightBegie">
            img
        </div>
        <div class="bg-darkBegie">
            forrás
        </div>
        <div class="bg-lightBegie">
            <button>Hirdetés szerkesztése</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
// interface ICarParams {
//   _id?: number;
//   kategoria_id?: number;
//   cim?: string;
//   evjarat?: string;
//   km_all?: number;
//   szin?: string;
//   uzemanyag?: string;
//   hengerurtartalom?: number;
//   teljesitmeny?: number;
//   serulesmentes?: boolean;
//   leiras?: string;
//   hirdetes_datum?: string;
//   vetelar: number;
//   kepek: string[];
// }
// // const props = defineProps<IParams>();
// const p = (defineProps<ICarParams>(), {
//   _id: 0,
//     kategoria_id: 0,
//     cim: "",
//     evjarat: "",
//     km_all: 0,
//     szin: "",
//     uzemanyag: "",
//     hengerurtartalom: 0,
//     teljesitmeny: 0,
//     serulesmentes: false,
//     leiras: "",
//     hirdetes_datum: "",
//     vetelar: 0,
//     kepek: [],
// });


const toggleValue = ref(false);
</script>

<style scoped>
.main {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin: 64px;
}

.bg-darkBegie {
    background-color: #c8be9c;
}

.bg-lightBegie {
    background-color: #ffe4c4;
}

.bg-darkBegie,
.bg-lightBegie {
    padding: 24px;
    width: 100%;
    height: fit-content;
    margin: 0;
    display: flex;
    justify-content: center;
    flex-direction: column;
}

button {
    background-color: #A5D6A7;
    padding: 7px;
    max-width: 160px;
    border: none;
    border-radius: 5px;
    box-shadow: #64625c 0px 1px 3px;
}
</style>
