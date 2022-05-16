<template>
  <v-container>
    <h1>Digi-Dex</h1>
    <div class="digiView">
      <MainCard v-for="digi in digimon" v-bind:key="digi" v:bind="digiData" />
    </div>
  </v-container>
</template>

<script>
import MainCard from "./Card.vue";

export default {
  name: "HomePage",
  digiData: {
    name: String,
    img: String,
    level: String,
  },
  components: {
    MainCard,
  },
  data() {
    return {
      digimon: [],
    };
  },
  mounted() {
    this.getAllDigis();
    console.log(this.digimon);
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
  },
};
</script>
