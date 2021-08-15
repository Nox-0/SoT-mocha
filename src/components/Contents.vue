<template>
  <div>
    <v-app-bar
      color="#6f7887"
      dense
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Secure your future with mindful saving</v-toolbar-title>

      <v-spacer></v-spacer>

<v-btn
        class="ma-2"
        color="#393E46"
        @click="overlay = !overlay"
        dark
      >
        Goals
        <v-icon
          dark
          center
        >
        </v-icon>
      </v-btn>

          <v-overlay
            :z-index="zIndex"
            :value="overlay"

          >
            <v-btn
              class="white--text"
              color="teal"
              @click="overlay = false"
            >
              Goals are set here!
            </v-btn>
          </v-overlay>

      <v-btn
              class="ma-2"
              color="#393E46"
              dark
            >
              Financial Wellbeing
              <v-icon
                dark
                center
              >
              </v-icon>
            </v-btn>

    <v-btn
        class="ma-2"
        color="#393E46"
        dark
      >
        Profile
        <v-icon
          dark
          center
        >
        </v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-wrench</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
          </v-btn>
        </template>

        <v-card flat>
                  <v-card-text v-text="text"></v-card-text>
                </v-card>

        <v-list>
          <v-list-item
            v-for="n in 5"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
  </div>
</template>

<script>
  export default {
    data: () => ({
      overlay: false,
      zIndex: 0,
      })
  }
</script>

<style>
v-toolbar-title{
    font-family: 'futura bold', sans-serif;

}
</style>