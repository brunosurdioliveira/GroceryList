<template>
  <v-app>
    <v-main>
      <v-container>
        <v-card class="mt-2 mx-auto my-12" max-width="850">
          <Header :groceries-not-gotten="groceriesNotGotten"></Header>
          <v-card-text>
            <GroceryControl @add="addNewGrocery" @clear-got="clearGottenItems" @clear-all="clearAllItems"></GroceryControl>
            <GroceryList :grocery-list="groceryList" @delete="deleteItem" @gotten="setGroceryGotten"></GroceryList>
          </v-card-text>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header";
import GroceryList from "./components/GroceryList";
import GroceryControl from "./components/GroceryControl";

export default {
  name: 'App',
  components: {
    GroceryControl,
    GroceryList,
    Header
  },
  data: () => ({
    groceryList: []
  }),
  computed: {
    groceriesNotGotten() {
      return this.groceryList.filter(item => !item.gotten).length;
    }
  },
  methods: {
    addNewGrocery(grocery) {
      this.groceryList.push(grocery)
    },
    clearGottenItems() {
      this.groceryList = this.groceryList.filter(item => !item.gotten)
    },
    clearAllItems() {
      this.groceryList = []
    },
    setGroceryGotten(index) {
      this.groceryList[index].gotten = !this.groceryList[index].gotten
    },
    deleteItem(index) {
      this.groceryList.splice(index, 1)
    }
  },
};
</script>
