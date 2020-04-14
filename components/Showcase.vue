<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      :width="width()"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          text
          color="deep-purple accent-4"
          v-on="on"
        >
          Showcase
        </v-btn>
      </template>

      <v-carousel
        cycle
        :height="height()"
        interval="5000"
        progress
        show-arrows
      >
        <v-carousel-item
          v-for="(image, i) in images"
          :key="i"
        >
          <v-img :src="image" />
        </v-carousel-item>
      </v-carousel>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: 'Showcase',
  props: {
    images: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data: () => ({
    dialog: false,
    width () {
      if (this.$vuetify.breakpoint.width > this.$vuetify.breakpoint.height) {
        return this.$vuetify.breakpoint.width / 100 * 44
      } else {
        return this.$vuetify.breakpoint.width / 100 * 90
      }
    },
    height () {
      if (this.$vuetify.breakpoint.width > this.$vuetify.breakpoint.height) {
        return this.$vuetify.breakpoint.height / 100 * 90
      } else {
        return this.$vuetify.breakpoint.height / 100 * 60
      }
    }
  })
}
</script>

<style scoped>

</style>
