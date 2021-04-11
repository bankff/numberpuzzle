<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-spacer>
        <div class="d-flex justify-center">
          <span class="font-weight-black justify-center" style="font-size: 3vh"
            >NumberPuzzle</span
          >
        </div></v-spacer
      >
      <router-link style="text-decoration: none; color: inherit;" to="/">
         <v-icon class="mx-auto pa-6">Home</v-icon>
      </router-link>
      <router-link style="text-decoration: none; color: inherit;" :to="{ name: 'setting', params: {time: 5 } }">
         <v-icon>Setting</v-icon>
      </router-link>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {
  },
};
</script>
