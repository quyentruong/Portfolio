<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      :width="$vuetify.breakpoint.width/100*44"
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
        :height="$vuetify.breakpoint.height/100*90"
        hide-delimiter-background
        show-arrows-on-hover
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
    colors: [
      'indigo',
      'warning',
      'pink darken-2',
      'red lighten-1',
      'deep-purple accent-4'
    ],
    slides: [
      'First',
      'Second',
      'Third',
      'Fourth',
      'Fifth'
    ]
  })
}
</script>

<style scoped>

</style>
