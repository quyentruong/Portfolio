<template>
  <div>
    <v-row align="center" justify="center">
      <Project />
    </v-row>
    <v-row align="center" justify="center">
      <Project />
    </v-row>
    <v-row align="center" justify="center">
      <Project />
    </v-row>

    <v-row align="center" justify="center">
      <Project />
    </v-row>
    <v-row>
      <TabSkills />
    </v-row>
  </div>
</template>

<script>
import TabSkills from '../components/Skills/TabSkills'
import Project from '../components/Project'

export default {
  components: { Project, TabSkills },
  data: () => ({
    tab: null
  })
}
</script>
