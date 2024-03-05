<template>
    <div class="main">
        <h5 class="bg-darkBegie"><b>{{p.car.cim}}</b></h5>

        <ul class="bg-lightBegie">
            <li>Szín: <b>{{p.car.szin}}</b></li>
            <li>Évjárat: <b>{{p.car.evjarat}}</b></li>
            <li>Hengerűrtartalom: <b>{{p.car.hengerurtartalom}} cm<sup>2</sup></b></li>
            <li>Hirdetés dátuma: <b>{{p.car.hirdetes_datum}}</b></li>
        </ul>

        <div class="bg-darkBegie">
            <p>
                {{leiras}}
            </p>
            <hr>
            <q-toggle v-model="toggleValue" @click="leirasToggle"/>
        </div>

        <div class="bg-lightBegie">
            <q-card-section v-if="p.car.kepek.length == 1" style="background-color: #ffe4c4">
            <div class="q-img q-img--menu" role="img" style="max-height: 200px">
                <div style="padding-bottom: 75%"></div>
                <div class="q-imgcontainer absolute-full">
                <img
                    aria-hidden="true"
                    class="q-imgimage q-imgimage--with-transition q-imgimage--loaded"
                    draggable="false"
                    fetchpriotity="auto"
                    loading="lazy"
                    :src="p.car.kepek[0]"
                    style="object-fit: scale-down; object-position: 50% 50%"
                />
                </div>
            </div>
            </q-card-section>
            <q-card-section v-if="p.car.kepek.length != 1" style="background-color: #ffe4c4">
            <q-carousel v-model="slide" style="height: 200px" thumbnails>
                <q-carousel-slide v-for="(item, idx) in p.car.kepek" :key="idx" :img-src="item" :name="idx + 1" />
            </q-carousel>
            </q-card-section>
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
const p = defineProps(["car","index"]);
const slide = ref(1);
const toggleValue = ref(false);
const teljesLeiras = p.car.leiras;
const leiras = ref();

function leirasToggle(){
    var count = 0;
    let szavak = teljesLeiras.split(" ")
    var l = ""
    szavak.forEach(szo => {
        if(count < 100){
            l+=szo+" "
        }
        for(var i = 0; i < szo.length; i++){
            count++;
        }
    });
    leiras.value = toggleValue.value == false ? l + "..." : teljesLeiras;
}
leirasToggle()
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
