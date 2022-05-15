<template>
  <v-container>
    <h1>Digi-Dex</h1>
    <div class="digiView">
      <img
        v-for="digi in digimon"
        v-bind:key="digi"
        width="50"
        height="50"
        :src="digi.img"
        :alt="digi.name"
      />
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
  mounted() {
    this.getAllDigis();
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
