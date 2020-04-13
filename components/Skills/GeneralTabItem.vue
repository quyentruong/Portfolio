<template>
  <div>
    <v-row v-for="item in sortItem" :key="item.name">
      <v-col class="mt-2">
        <v-label>{{ item.name }}</v-label>
      </v-col>
      <v-col>
        <v-rating
          :length="10"
          :value="item.value"
          empty-icon="mdi-emoticon-outline"
          full-icon="mdi-emoticon"
          readonly
          color="blue lighten-1"
          background-color="grey lighten-1"
          dense
        />
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'GeneralTabItem',
  props: {
    items: {
      type: Array,
      default () {
        return []
      }
    }
  },
  computed: {
    sortItem () {
      const items = this.items
      return items.sort((a, b) => b.value - a.value || a.name.localeCompare(b.name))
    }
  }
}
</script>

<style scoped>

</style>
