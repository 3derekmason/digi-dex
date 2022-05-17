<template>
  <div class="toolbar">
    <v-select
      :items="attributes"
      @update:modelValue="this.changeOrder"
      label="Order By:"
      class="d-select"
    ></v-select>
  </div>
</template>

<script>
export default {
  name: "MainToolbar",
  props: {
    digimon: Array,
  },
  data: () => {
    return {
      attributes: ["Level", "Name"],
    };
  },
  methods: {
    changeOrder: (e) => {
      return e === "Name" ? this.orderByName(this.digimon) : console.log(e);
    },
    orderByName: (array) => {
      array.sort((a, b) => {
        const nameA = a.name.toUpperCase();
        const nameB = b.name.toUpperCase();
        return nameA < nameB ? -1 : nameA > nameB ? 1 : 0;
      });
    },
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
