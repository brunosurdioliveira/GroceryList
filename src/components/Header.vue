<template>
  <v-toolbar
      color="#D2F6D2"
      elevation="0"
  >
    <v-icon class="mr-2">mdi-cart</v-icon>
    <v-toolbar-title>Grocery List
      <small v-if="groceriesNotGotten > 0" class="font-weight-light">({{ groceriesNotGotten }})</small>
    </v-toolbar-title>
  </v-toolbar>
</template>

<script>
export default {
  name: "Header",
  props: {
    groceriesNotGotten: {
      type: Number
    },
  },
}
</script>

<style scoped>

</style>
