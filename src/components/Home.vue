<template>
  <AppBar />
  <div class="homePage">
    <div class="toolbar">
      <v-select
        :items="attributes"
        @update:modelValue="changeOrder"
        label="Order By:"
        class="d-select"
      ></v-select>
    </div>
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
      attributes: ["Name", "Level"],
    };
  },
  mounted() {
    this.getAllDigis();
  },
  methods: {
    async getAllDigis() {
      this.digimon.splice(0);
      const res = await fetch("https://digimon-api.vercel.app/api/digimon");
      const data = await res.json();
      data.forEach((digi) => {
        this.digimon.push(digi);
      });
    },
    sortByName(arr) {
      arr.sort((a, b) => {
        const nameA = a.name.toUpperCase();
        const nameB = b.name.toUpperCase();
        return nameA < nameB ? -1 : nameA > nameB ? 1 : 0;
      });
    },
    changeOrder(e) {
      return e === "Name"
        ? this.sortByName(this.digimon)
        : e === "Level"
        ? this.getAllDigis()
        : console.log("err");
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

.toolbar {
  padding: 0;
  margin-top: 8px;
  width: 20%;
  height: 56px;
  background: #a9aabc;
  border-radius: 4px;
}
.d-select {
  border-radius: 4px;
  text-align: center;
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
