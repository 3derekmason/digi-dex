<template>
  <div class="digiCard">
    <p>{{ this.cardName }}</p>
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
  data() {
    return {
      cardName: this.name,
      cardImg: this.img,
      cardType: this.type,
    };
  },
};
</script>
