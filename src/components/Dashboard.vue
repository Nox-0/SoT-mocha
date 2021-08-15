<template>
  <v-container>
    <v-row>
      <v-col
          v-for="card in cards"
          :key="card"
      :card="card">
        <v-card
            :loading="loading"
            max-width="374">
          <v-img
              height="250"
              src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          ></v-img>
          <v-progress-linear
          :value="card.id">
          </v-progress-linear>
          <v-card-title>{{card.goal}}</v-card-title>
          <v-card-subtitle>${{card.amount}}<br/>{{card.date}}</v-card-subtitle>
          <v-card-actions>
            <v-container>
              <v-dialog max-width="750px"
                        v-model="dialog">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                      color="blue"
                      dark
                      v-bind="attrs"
                      v-on="on">
                    Add input
                  </v-btn>
                </template>
                <v-card>
                  <v-card-title>
                    Add input to card
                  </v-card-title>
                  <v-card-text>
                    <v-container>
                      <v-row>
                        <v-col>
                          <h2>Goal Name</h2>
                        </v-col>
                        <v-col>
                          <v-select
                              v-model="goal"
                              :items="goals"
                              label="Choose a goal"
                              outlined>
                          </v-select>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <h2>Target Amount</h2>
                        </v-col>
                        <v-col>
                          <v-text-field
                              v-model="amount"
                              required
                              label="$">
                          </v-text-field>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <h2>Time Set</h2>
                        </v-col>
                        <v-col>
                          <v-date-picker
                              required
                              v-model="picker"></v-date-picker>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-select
                            v-model="business"
                            :items="businesses"
                            label="Add Voucher"
                            outlined>
                        </v-select>
                      </v-row>
                      <v-row>
                        <v-col>
                          <v-checkbox
                              v-model="checkbox"
                              :label="`Send the gift voucher to my email address`"
                          ></v-checkbox>
                        </v-col>
                        <v-col>
                          <v-btn align="left"
                                 @click="forminputfunc(card.id)">
                            Add
                          </v-btn>
                        </v-col>
                      </v-row>
                    </v-container>
                  </v-card-text>
                </v-card>
              </v-dialog>
            </v-container>
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
    </v-card>
  </v-container>
</template>

<script>

export default {
  name: "Dashboard.vue",

  data: () => ( {
    dialog: false,
    loading: false,
    cards: [],
    card: null,
    goal: null,
    amount: "",
    business: null,
    checkbox: null,
    businesses: ["ANZ", "AA", "House of Travel", "Countdown", "Pak'n'Save", "The Warehouse"],
    goals: ["Car", "House", "Travel"],
    picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
  }),

  methods: {
    add () {
      this.loading = true
      setTimeout(() => (this.loading = false), 2000)
      let card = {
        id: 0,
        goal: "Sample title",
        img_path: "https://cdn.vuetifyjs.com/images/cards/cooking.png",
        amount: 0,
        business: null,
        checkbox: null,
        loading: false,
        date: new Date(Date.now()),
      }
      if (this.cards.length == 0) {
        this.cards.push(card)
      } else {
        card.id = this.cards[this.cards.length-1].id+1
        this.cards.push(card)
      }
      console.log(this.cards)

    },

    forminputfunc (id) {
      let card = this.cards[id]
      console.log(card)
      card.goal = this.goal;
      card.amount = this.amount;
      card.business = this.business;
      card.checkbox = this.checkbox;
      card.date = this.picker;

      this.$set(this.cards, id, card)
      console.log(this.cards)
      this.dialog = false;
    },

  }
}
</script>

<style scoped>

</style>