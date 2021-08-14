<template>
  <v-card>
    <v-toolbar
      color="cyan"
      dark
      flat
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Money Coach. Secure your future with mind for spending.</v-toolbar-title>

      <v-spacer></v-spacer>

<v-btn
        class="ma-2"
        color="cyan"
        @click="overlay = !overlay"
        dark
      >
        Goals
        <v-icon
          dark
          right
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
              color="cyan"
              dark
            >
              Financial Wellbeing
              <v-icon
                dark
                right
              >
              </v-icon>
            </v-btn>

    <v-btn
        class="ma-2"
        color="cyan"
        dark
      >
        User ID
        <v-icon
          dark
          right
        >
        </v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-wrench</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-minus-circle</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          v-model="tab"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>

          <v-tab
            v-for="item in items"
            :key="item"
          >
            {{ item }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tab">
      <v-tab-item
        v-for="item in items"
        :key="item"
      >
        <v-card flat>
          <v-card-text v-text="text"></v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      overlay: false,
      zIndex: 0,
    }),
  }
</script>