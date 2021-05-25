<template>
  <q-page class="flex flex-center q-pa-md row items-start q-gutter-md">
    
    <q-card class="my-card" v-for="(personaje, i) in personajes" :key="i">
      <img :src="personaje.image" />

      <q-card-section>
        <div class="text-h6">{{personaje.name}}</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import axios from "app/node_modules/axios";
export default {
  name: "PageIndex",

  data() {
    return {
      personajes: []
    };
  },
  methods: {
    async getData() {
      const url = "https://rickandmortyapi.com/api/character";
      try {
        const req = await axios(url);
        this.personajes = req.data.results;
      } catch (error) {
        console.log(error);
      }
    }
  },
  created() {
    this.getData();
  }
};
</script>