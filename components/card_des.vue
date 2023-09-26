<template>
    <v-card class="card-container">
        <v-row>
            <v-img class="card-img" :src="pjs.thumbnail.path + '.' + pjs.thumbnail.extension" alt={{pjs.name}} />
        </v-row>

        <v-col>
            <v-row class="header">
                {{ pjs.name }}
            </v-row>
            <v-row>
                <v-col>
                    <v-card elevation-15 class="details">
                        <ul>
                            <li class="li"> Cantidad de comics: {{ pjs.comics.available }} </li> <br>
                            <li class="li"> Cantidad de series: {{ pjs.series.available }} </li> <br>
                            <v-row text-align="center" color="#000" v-for=" (serie, index) in pjs.series.items"
                                :key="index">
                                <v-col cols="12" v-if="index < 3">
                                    <h2 class="li"> {{ index + 1 }}. {{ serie.name }}</h2>
                                </v-col>
                            </v-row>
                            <br>
                            <li class="li"> Cantidad de historias: {{ pjs.stories.available }} </li> <br>
                            <li class="li"> Cantidad de eventos: {{ pjs.events.available }} </li>
                        </ul>
                    </v-card>
                    <br>
                    <v-row class="description">
                        <li class="li"> Descripción: {{ pjs.description || "No cuenta con descripción"}}</li>
                    </v-row>
                </v-col>
            </v-row>
        </v-col>
    </v-card>
</template>



<script>
export default {
    props: {
        pjs: Object
    }
}
</script>


<style>
.card-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    margin: 3rem;
    width: 70dvw;
    height: 100dvh;
}

.card-container>* {
    min-width: 25rem;
    max-width: 40rem;
}

.card-img {
    flex: 1 0;
    object-fit: cover;
    height: 50rem;
    margin: 2rem;
}

.header {
    font-size: 23px;
    align-items: center !important;
    margin: auto !important;
    color: rgb(255, 0, 0)
}

.details {
    display: flex !important;
    justify-content: center !important;
    flex-direction: column !important;
    height: 340px !important;
    margin-top: 45px !important;
}

::-webkit-scrollbar {
    width: 28px;
    background: transparent;
}

::-webkit-scrollbar-thumb {
    box-shadow: inset 0 0 0 10px #c9c6c6;
    border: 10px solid transparent;
    border-radius: 40px;
}

.description {
    width: 65%
}
</style>