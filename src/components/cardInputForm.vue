<template>
  <v-container>
    <v-dialog max-width="750px">
      <template v-slot:activator="{ on, attrs}">
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
                <v-text-field required>
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
                <v-btn align="left">
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
  data () {
    return {
      picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
    }
  }
}
</script>

<style scoped>
$date-picker-table-height: 100px !default;

</style>