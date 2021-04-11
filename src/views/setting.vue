<template>
  <div class="setting d-flex justify-center">
    <v-col cols="12" sm="6">
      <v-text-field
        name="input"
        style="font-size: 1.9em"
        label="Setting Timeout"
        :value="time"
        ref="input"
      ></v-text-field>
    </v-col>
    <v-card-actions class="justify-center">
      <v-btn
        x-large
        color="info"
        class="ma-2 white--text"
        v-on:click="setTime()"
      >
        บันทึก
      </v-btn>
    </v-card-actions>
  </div>
</template>
<script>
/* eslint-disable */
import Vue from "vue";
import store from '../store'

export default Vue.extend({
  name: "setting",
    data: () => ({
    time:(store.state.time/1000)/60,
  }),
  methods:{
    setTime:function (){
      store.commit('setTime',parseInt(document.querySelector("input").value*60*1000))
    }
  }
});
</script>
