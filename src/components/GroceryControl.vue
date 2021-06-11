<template>
  <v-container>
    <v-text-field append-outer-icon="mdi-send" filled label="Grocery Item" type="text"
                  v-model="newGrocery"
                  @keyup.enter="addNewGrocery()"
                  @click:append-outer="addNewGrocery()"
    ></v-text-field>
    <div class="text-right">
      <v-btn color="primary" @click="$emit('clear-got')">
        <v-icon
            left
            dark
        >
          mdi-check-outline
        </v-icon>
        Clear Got Grocery Items
      </v-btn>
      <v-btn color="error" class="ml-2" @click="$emit('clear-all')">
        <v-icon
            left
            dark
        >
          mdi-delete
        </v-icon>
        Clear All Grocery Items
      </v-btn>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "GroceryControl",
  data() {
    return {
      newGrocery: '',
    }
  },
  methods: {
    addNewGrocery() {
      if (this.newGrocery) {
        const grocery = {name: this.newGrocery, gotten: false}
        this.$emit('add', grocery)
        this.newGrocery = ''
      }
    }
  },
}
</script>

<style scoped>

</style>
