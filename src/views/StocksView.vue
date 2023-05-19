<script>
import Stock from '../components/stocks/StockComponent.vue'

export default {
  components: { Stock },
  computed: {
    stocks() {
      return this.$store.getters.stocks
    }
  }
}
</script>

<template>
  <v-container>
    <v-col cols="12" md="6" lg="12">
      <v-row>
        <Stock v-for="stock in stocks" :key="stock.id" :stock="stock"/>
      </v-row>
    </v-col >
</v-container>
</template>

<style>

</style>