<template>
    <v-container class="container">
        <v-row>
            <v-col v-for="item in pj" :key="item.id" cols="12" sm="4">
                <v-card class="card">
                    <v-img :src="item.thumbnail.path + '.' + item.thumbnail.extension" height="200px" cover></v-img>

                    <v-card-title>
                        {{ item.name }}
                    </v-card-title>

                    <v-card-subtitle>
                        Información provista de Marvel
                    </v-card-subtitle>

                    <v-card-actions>
                        <v-btn color="red" variant="text" @click="description(item)">
                            Ver detalles
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
            <v-card >
                <v-dialog v-model="select" width="auto">
                    <card-des :pjs="actualPj"></card-des>
                    <v-btn color="red" class="btn" block @click="select = false">Cerrar</v-btn>
                </v-dialog>
            </v-card>
        </v-row>
    </v-container>
</template>


<script setup>

import card_des from '~/components/card_des.vue';
import axios from 'axios';

onBeforeMount(() => {
    getPj();
});

const publicKey = "9539ecefd340b9d803c69098e8df8e42";
const hash = "9e00f50b0adbc9dd4de620222f97fe6d";
const url = `https://gateway.marvel.com:443/v1/public/characters?ts=7&apikey=${publicKey}&hash=${hash}&limit=100`;
const pj = ref([]);
const actualPj = ref(null);

const select = ref(false);

const getPj = async () => {
    const { data } = await axios.get(url)
    pj.value = data.data.results.filter(pjs => {
        return !pjs.thumbnail.path.includes("Imagen no disponible");
    })

}
const description = (pjs) => {
    actualPj.value = pjs;
    select.value = true;
}

</script>


<style>
.container {
    margin-top: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
}

.card {
    margin: 1rem;
    max-width: 344;
}

.img {
    object-fit: cover;
    height: 14.5rem;
}
</style>