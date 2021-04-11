<template>
  <div>
    <v-card width="80" height="80" :color="colors" outlined rounded
      ><v-card-title class="justify-center ma-2" style="font-size: 2.4vh">{{
        numbers
      }}</v-card-title></v-card
    >
  </div>
</template>

<script>
export default {
  name: "card",
  props: {
    number: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      numbers: this.number,
      colors: this.color,
    };
  },
  watch: {
    number() {
      this.numbers = this.number;
    },
  },
};
</script>

<style>
</style>