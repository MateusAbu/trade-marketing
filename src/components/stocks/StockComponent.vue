<script>
  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0,
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds
      },
      insufficientFunds() {
        return this.quantity * this.stock.price > this.funds
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity,
        }
        this.$store.dispatch('buyStock', order)
        this.quantity = 0 
      }
    }
  }
</script>

<template>
  <div class="flex pr-3 pb-3">
    <v-card color='green' class="white--text">
      <v-card-title class="headline">
        <strong>{{ stock.name }} <small>(Price: ${{ stock.price }})</small></strong>
      </v-card-title>
    </v-card>
    <v-card>
      <v-container>
        <v-row align="center">
          <v-text-field label="Quantidade" type="number" class="pr-3" v-model.number="quantity" :error="insufficientFunds|| quantity < 0 || !Number.isInteger(quantity)" />
          <v-btn :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)" 
          @click="buyStock" color='green' class="white--text">
          {{ insufficientFunds ? 'Insufficient' : 'Buy' }} 
          </v-btn>
        </v-row>
      </v-container>
    </v-card>
  </div>
</template>

<style>

</style>