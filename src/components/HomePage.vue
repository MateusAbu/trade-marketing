<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds
      }
    }
  }
</script>

<template>
  <div>
    <h1 class="text-h3 font-weight-light mb-4">Trade and Consult your Actions!</h1>
    <v-sheet :elevation="6" class="pa-2" color="primary">
      <v-icon class="mr-3" color="white">mdi-information</v-icon>
      <span class="text-h6">You can load and save the Data</span>
    </v-sheet>
    <v-sheet :elevation="6" class="pa-2 mt-3" color="success">
      <v-icon class="mr-3" color="white">mdi-information</v-icon>
      <span class="text-h6">Click in 'End the Day' to start another Day! </span>
    </v-sheet>
    <v-divider class="my-4"/>
    <p class="text-h5"><strong>Your Balance: </strong>${{ funds }}</p>
  </div>
</template>

<style>

</style>