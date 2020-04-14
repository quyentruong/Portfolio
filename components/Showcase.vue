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
          v-for="(image, i) in filterImage(images)"
          :key="i"
        >
          <img v-lazy-load :data-src="require(`../assets/showcase/${image.pathShort}`)" :width="width()" :height="height()">
          <!--          <v-img :max-width="width()" :max-height="height()" contain :src="image.pathLong" />-->
        </v-carousel-item>
      </v-carousel>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: 'Showcase',
  props: {
    folder: {
      type: String,
      default: 'mudbay'
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
    },
    images: []
  }),
  mounted () {
    this.importAll(require.context('../assets/showcase/', true, /\.png|.jpg$/))
  },
  methods: {
    importAll (r) {
      r.keys().forEach(key => (this.images.push({ pathLong: r(key), pathShort: key.replace('./', '') })))
    },
    filterImage (images) {
      return images.filter(image => image.pathShort.includes(this.folder))
    }
  }
}
</script>

<style scoped>

</style>
