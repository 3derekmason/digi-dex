<template>
  <AppBar />
  <div class="homePage">
    <MainToolbar :digimon="this.digimon" />
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
import MainToolbar from "./Toolbar.vue";

export default {
  name: "HomePage",
  components: {
    MainCard,
    AppBar,
    AppFoot,
    MainToolbar,
  },
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
      });
      await this.digimon.sort((a, b) => {
        const nameA = a.name.toUpperCase();
        const nameB = b.name.toUpperCase();
        return nameA < nameB ? -1 : nameA > nameB ? 1 : 0;
      });
    },
  },
};
</script>

<style scoped>
.homePage {
  width: 100vw;
  height: calc(100vh - 117px);
  background: #454655;
  overflow-y: scroll;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}

.digiView {
  width: 90vw;
  height: calc(100vh - 181px);
  border-radius: 2px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 16px;
  overflow-y: scroll;
}
</style>
