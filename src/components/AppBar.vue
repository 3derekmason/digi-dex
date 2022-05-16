<template>
  <v-app-bar>
    <v-app-bar-title class="title">Digi Dex</v-app-bar-title>
  </v-app-bar>
</template>

<script>
export default {
  name: "AppBar",
};
</script>

<style scoped>
.v-app-bar {
  background: #0d47a1;
  color: #fff;
  text-align: center;
}
.title {
  letter-spacing: 8px;
  font-size: 2em;
  font-weight: 500;
  font-variant: small-caps;
}
</style>
