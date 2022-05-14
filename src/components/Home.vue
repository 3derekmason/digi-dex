<template>
  <v-container>
    <h1>Digi-Dex</h1>
    <v-btn v-on:click="getAllDigis">Test</v-btn>
  </v-container>
</template>

<script>
export default {
  name: "HomePage",
  data() {},
  methods: {
    getAllDigis: async () => {
      const res = await fetch("https://digimon-api.vercel.app/api/digimon");
      const data = await res.json();
      console.log(data);
    },
  },
};
</script>
