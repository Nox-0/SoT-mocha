<template>
  <v-container>
    <v-dialog max-width="750px">
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
                @click="forminputfunc">
                  Add
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  name: "cardInputForm.vue",
  props: ["card"],
  data () {
    return {
      goal: null,
      amount: "",
      business: null,
      checkbox: null,
      businesses: ["ANZ", "AA", "House of Travel", "Countdown", "Pak'n'Save", "The Warehouse"],
      goals: ["Car", "House", "Travel"],
      picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
    }
  },
  methods: {
    forminputfunc () {
      var formInput = {}
      formInput.id = this.card.id;
      formInput.goal = this.goal;
      formInput.amount = this.amount;
      formInput.date = this.picker;
      formInput.business = this.business;
      formInput.checkbox = this.checkbox;
      console.log(formInput)
      this.$emit('inputted', formInput)
    }
  }
}
</script>

<style scoped>

</style>