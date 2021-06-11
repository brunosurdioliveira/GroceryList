<template>
  <v-list flat>
    <v-list-item-group>
      <template v-for="(grocery, index) in groceryList" >
        <v-list-item :key="index">
          <v-list-item-content @click="setGotten(index)">
            <v-list-item-title :class="{'text-decoration-line-through': grocery.gotten}">
              {{ grocery.name }}
            </v-list-item-title>
          </v-list-item-content>
          <v-list-item-action>
            <v-icon color="error" @click="deleteItem(index)">
              mdi-close
            </v-icon>
          </v-list-item-action>
        </v-list-item>
        <v-divider :key="'divider'+index"></v-divider>
      </template>
    </v-list-item-group>
  </v-list>
</template>

<script>
export default {
  name: "GroceryList",
  props: {
    groceryList: {
      type: Array,
    },
  },
  methods: {
    deleteItem(index) {
      this.$emit('delete', index)
    },
    setGotten(index) {
      this.$emit('gotten', index)
    }
  },
}
</script>

<style scoped>

</style>
