<template>
  <div>
    <v-app-bar
      color="cyan"
      dense
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Secure your future with mind for spending</v-toolbar-title>

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
              color="cyan"
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
        color="cyan"
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