<template>
  <v-container>
    <h1>Digi-Dex</h1>
    <v-btn v-on:click="getAllDigis">Fetch</v-btn>
    <v-btn v-on:click="showDigis">Show</v-btn>
    <div class="digiView">
      <img v-for="digi in digimon" v-bind:key="digi" :src="digi.img" />
    </div>
  </v-container>
</template>

<script>
export default {
  name: "HomePage",
  data() {
    return {
      digimon: [],
    };
  },
  methods: {
    async getAllDigis() {
      const res = await fetch("https://digimon-api.vercel.app/api/digimon");
      const data = await res.json();
      data.forEach((digi) => {
        this.digimon.push(digi);
        console.log("fetched");
      });
    },
    showDigis() {
      console.log(this.digimon);
    },
    getPhoto() {
      return this.img;
    },
  },
};
</script>
