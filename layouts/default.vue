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
    <v-content class="background">
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
export default {
  data () {
    return {
      title: 'Quyen Truong Portfolio'
    }
  }
}
</script>
<style>
  .background {
    background-image: url('https://www.nasa.gov/sites/default/files/thumbnails/image/stsci-h-p2001a-m-2000x1500_0.png');
    background-repeat: round;
  }
  .centerElement {
    margin-right: auto;
    margin-left: auto;
  }
</style>
