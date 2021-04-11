<template>
  <v-card class="mx-auto pa-4" max-width="500">
    <v-card-title
      class="font-weight-black justify-center"
      style="font-size: 7vh"
      >{{ parseInt((time/1000)/60) }}:{{ (time/1000)%60}}</v-card-title
    >

    <v-card-actions class="justify-center ma-2">
      <v-btn color="orange" text v-on:click="active ? timer() : stop()">
        {{ active ? "start" : "stop" }}
      </v-btn>

      <v-btn color="orange" text v-on:click="resetTime()"> Reset </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import store from '../store'

export default {
  name: "Timer",
  data() {
    return {
      timeOut:null,
      time:store.state.time,
      active: true,
    };
  },
  methods: {
    stop: function () {
      try {
        clearInterval(this.timeOut);
        this.active = true;
      } catch (error) {
        console.log(error);
      }
    },
    timer: function () {
      this.active = false;
      this.timeOut = setInterval(() => {
        this.time-=1000;
        if (this.time === 0) {
          clearInterval(this.timeOut);
        }
      }, 1000);
    },
    resetTime: function () {
      try {
        this.active = true;
        clearInterval(this.timeOut);
        this.time =store.state.time;
        // to do this func
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
</style>