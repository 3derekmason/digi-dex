<template>
  <div class="digiCard">
    <p>{{ this.name }}</p>
    <img :src="this.img" width="80" />
    <p>{{ this.level }}</p>
  </div>
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
