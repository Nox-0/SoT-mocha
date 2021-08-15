<template>
  <v-container>
    <v-row>
      <v-col
          v-for="card in cards"
          :key="card">
        <v-card
            :loading="loading"
            max-width="374">
          <template slot="progress">
          </template>
          <v-img
              height="250"
              :src="card.img_path"
          ></v-img>
          <v-progress-linear
                color="blue"
                height="10"
                :value=card.percentage
            ></v-progress-linear>
          <v-card-title>{{card.title}}</v-card-title>
          <v-card-subtitle>{{card.id}}</v-card-subtitle>
          <v-card-actions>
            <v-btn
                color="blue"
                text
                @click="add">
              Add
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>

    <v-card
        :loading="loading"
        max-width="374"
        @click="add"
    >
      <template slot="progress">
        <v-progress-linear
            color="blue"
            height="10"
            indeterminate
        ></v-progress-linear>
      </template>
      <v-img
          height="250"
          src="https://www.pinclipart.com/picdir/middle/40-402458_sign-clipart-addition-blue-plus-sign-png-transparent.png"
      ></v-img>
      <v-card-title>Add New Goal</v-card-title>
      <v-card-actions>
        <v-btn
            color="blue"
            text
            @click="add">
          Add
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "Dashboard.vue",

  data: () => ( {
    loading: false,
    cards: [],
  }),

  methods: {
    add () {
      this.loading = true
      setTimeout(() => (this.loading = false), 2000)
      var card = {
        id: 0,
        title: "Sample title",
        img_path: "https://cdn.vuetifyjs.com/images/cards/cooking.png",
        loading: false,
        percentage: 20,
      }

      if (this.cards.length == 0) {
        this.cards.push(card)
      } else {
        card.id = this.cards[this.cards.length-1].id+1
        card.percentage = card.percentage * card.id
        this.cards.push(card)        
      }
      console.log(this.cards)

    },


  }
}
</script>

<style scoped>

</style>