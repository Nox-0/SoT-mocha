<template>
  <v-app>
    <v-app-bar
        app
        color="#393E46"
        dark
    >
      <div class="d-flex align-center">

        <img src="./assets/Artboard 1.png"
             width="300"
        />
      </div>
    </v-app-bar>

    <v-main>
      <Contents/>
      <infobox/>
      <Dashboard/>
    </v-main>
  </v-app>
</template>

<script>
import Contents from '@/components/Contents';
import infobox from '@/components/infobox';
import Dashboard from "@/components/Dashboard";

export default {
  name: 'App',

  components: {
    Contents,
    infobox,
    Dashboard
  },

  data: () => ({
    //
  }),
};
</script>
