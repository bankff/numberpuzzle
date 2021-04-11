<template>
  <v-card class="mx-auto pa-6" width="400" elevation="0" style="margin: 100px">
    <v-list-item three-line class="justify-center">
      <v-card width="500" height="80" outlined>
        <v-card-title
          class="font-weight-black justify-center ma-2"
          style="font-size: 7vh"
          >{{parseInt(number/100)}}</v-card-title
        >
      </v-card>
      <v-card width="500" height="80" outlined>
        <v-card-title
          class="font-weight-black justify-center ma-2"
          style="font-size: 7vh"
          >{{parseInt((number%100)/10)}}</v-card-title
        >
      </v-card>
      <v-card width="500" height="80" outlined>
        <v-card-title
          class="font-weight-black justify-center ma-2"
          style="font-size: 7vh"
          >{{number%10}}</v-card-title
        >
      </v-card>
    </v-list-item>

    <v-card-actions class="justify-center">
      <v-btn x-large color="info" class="ma-2 white--text" v-on:click="randomNumber(10,99)">
        สุ่มเลข 2 หลัก
      </v-btn>
      <v-btn x-large color="success" class="ma-2 white--text" v-on:click="randomNumber(100,999)">
        สุ่มเลข 3 หลัก
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import {EventBus} from "../bus.ts"
export default {
  components: {},
  data() {
    return {
      number:0,
    }
  },
  methods:{
    randomNumber:async function(min,max){
      try {
        this.number = parseInt(Math.random()* (max - min) + min);
        this.replyActionRandom();
      } catch (error) {
        console.log();
      }
    },
    replyActionRandom:async function(){
      try {
        EventBus.$emit("Random");
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style>
</style>