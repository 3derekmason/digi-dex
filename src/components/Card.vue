<template>
  <v-card elevation="3" class="digiCard">
    <v-card-title class="digiName">{{ this.name }}</v-card-title>
    <img :src="this.img" class="digiPic" />
    <v-card-text class="digiLevel">{{ this.level }}</v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "MainCard",
  props: {
    name: String,
    img: String,
    level: String,
  },
};
</script>

<style scoped>
.digiCard {
  box-sizing: border-box;
  padding: 24px;
  width: 200px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.digiPic {
  width: 80%;
}
.v-card-text,
.v-card-title {
  padding: 0;
}
</style>
