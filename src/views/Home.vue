<template>
  <v-container fluid>
    <v-row align="center">
      <v-col sm="8">
        <v-row no-gutters v-for="(number, index) in numbers" :key="index">
          <template v-for="(n, i) in number">
            <v-col :key="i" sm="1">
              <Card
                :number="n"
                :color="
                  index + i == index * 2 || index + i == 9
                    ? 'lime lighten-2'
                    : ''
                "
              />
            </v-col>
          </template>
        </v-row>
      </v-col>
      <v-col sm="3">
        <Timer />
        <Random-number @Random="random" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Vue from "vue";
import Card from "@/components/card.vue";
import RandomNumber from "@/components/randomNumber.vue";
import Timer from "@/components/Timer.vue";
import { EventBus } from "../bus.ts";
import store from "../store";

export default Vue.extend({
  name: "Home",
  components: {
    Card,
    Timer,
    RandomNumber,
  },
  data: () => ({
    //
    count: 0,
    numbers: [],
  }),
  methods: {
    random: function () {
      this.numbers = [];
      for (let index = 0; index < 10; index++) {
        this.numbers.push([]);
        for (let i = 0; i < 10; i++) {
          this.numbers[index].push(parseInt(Math.random() * 10));
        }
      }
    },
  },
  created: function () {
    this.random();
  },
  mounted: function () {
    EventBus.$on("Random", () => {
      for (let index = 0; index < 100; index++) {
        this.random();
      }
    });
  },
});
</script>
