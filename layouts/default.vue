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
      title: 'Quyen Truong Portfolio ' + this.$vuetify.breakpoint.name,
      backgroundURL: require('../assets/background.png')
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
