<template>
  <AppBar />
  <div class="homePage">
    <v-container class="digiView">
      <MainCard
        v-for="digi in digimon"
        v-bind:key="digi"
        :name="digi.name"
        :img="digi.img"
        :level="digi.level"
      />
    </v-container>
  </div>
  <AppFoot />
</template>

<script>
import MainCard from "./Card.vue";
import AppBar from "./AppBar.vue";
import AppFoot from "./Footer.vue";

export default {
  name: "HomePage",
  components: {
    MainCard,
    AppBar,
    AppFoot,
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

<style scoped>
.homePage {
  width: 100vw;
  background: #454655;
  overflow-y: scroll;
}

.digiView {
  width: 90vw;
  height: calc(100vh - 117px);
  border-radius: 2px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 16px;
  overflow-y: scroll;
}
</style>
