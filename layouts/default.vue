<template>
  <v-app dark>
    <v-app-bar
      clipped-left
      fixed
      app
      scroll-off-screen
    >
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-content class="background" :style="{ backgroundImage: `url(${backgroundURL})` }">
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-btn
      v-show="fab"
      v-scroll="onScroll"
      fab
      fixed
      bottom
      right
      color="primary"
      @click="toTop"
    >
      <v-icon>mdi-chevron-up</v-icon>
    </v-btn>
    <v-footer
      fixed
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
// import { routerOptions } from '../.nuxt/router'

export default {
  data () {
    return {
      title: 'Quyen Truong Portfolio',
      backgroundURL: require('../assets/background.png'),
      fab: false
    }
  },
  methods: {
    onScroll (e) {
      if (typeof window === 'undefined') { return }
      const top = window.pageYOffset || e.target.scrollTop || 0
      this.fab = top > 20
    },
    toTop () {
      this.$vuetify.goTo(0)
    }
  }
}
</script>
<style>
  .background {
    background-repeat: round;
  }
  .centerElement {
    margin-right: auto;
    margin-left: auto;
  }
</style>
