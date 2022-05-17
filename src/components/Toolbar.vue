<template>
  <div class="toolbar">
    <v-select :items="attributes" label="Order By:" class="d-select"></v-select>
  </div>
</template>

<script>
export default {
  name: "MainToolbar",
  data: () => {
    return {
      attributes: ["Level", "Name"],
    };
  },
  props: {
    digimon: Array,
  },
};
</script>

<style scoped>
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
</style>
