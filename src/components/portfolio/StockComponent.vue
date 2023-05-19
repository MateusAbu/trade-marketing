<script>
  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0,
      }
    },
    computed: {
      insufficientQuantity() {
        return this.quantity > this.stock.quantity
      }
    },
    methods: {
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity,
        }
        this.$store.dispatch('sellStock', order)
        this.quantity = 0 
      }
    }
  }
</script>

<template>
  <div class="flex pr-3 pb-3">
    <v-card color='blue' class="white--text">
      <v-card-title class="headline">
        <strong>{{ stock.name }} <small>(Price: ${{ stock.price }}) | Quantity: {{ stock.quantity }}</small> </strong>
      </v-card-title>
    </v-card>
    <v-card>
      <v-container>
        <v-row align="center">
          <v-text-field label="Quantidade" type="number" class="pr-3" v-model.number="quantity" :error="insufficientQuantity || !Number.isInteger(quantity)"/>
          <v-btn :disabled="quantity <= 0 || insufficientQuantity || !Number.isInteger(quantity)" 
          @click="sellStock" color='blue' class="white--text">
          {{ insufficientQuantity ? 'insufficient' : 'Sell' }}
          </v-btn>
        </v-row>
      </v-container>
    </v-card>
  </div>
</template>

<style>

</style>