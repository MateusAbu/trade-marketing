<script>
  import { mapActions } from 'vuex'

  export default {
    computed: {
      funds() {
        return this.$store.getters.funds
      }
    },
    methods: {
      ...mapActions(['randomizeStocks']),
      endDay() {
        this.randomizeStocks()
      }
    }
  }
</script>

<template>
    <v-toolbar app>
      <v-toolbar-title class=" font-weight-bold text-uppercase">
        <span>Trade</span>
        <span class="font-weight-light">Market</span>
      </v-toolbar-title>
      <v-toolbar-items>
        <v-btn flat to="/">Home</v-btn>
        <v-btn flat to="/portfolio">Portfolio</v-btn>
        <v-btn flat to="/stocks">Stocks</v-btn>
      </v-toolbar-items>

      <v-spacer></v-spacer>

      <v-toolbar-items>
        <v-btn @click="endDay" flat>End the Day</v-btn>
        <v-menu offset-y>
          <template v-slot:activator="{ props }">
            <v-btn flat
              v-bind="props"
            >
              Load & Save
            </v-btn>
          </template>

          <v-list>
            <v-list-item>
              <v-list-item-title> Save Data </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title> Load Data </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-toolbar-items>
          <v-btn class="text-grey-darken-2" flat>Your Balance: ${{ funds }}</v-btn>
        </v-toolbar-items>
      </v-toolbar-items>
    </v-toolbar>
</template>

<style>

</style>