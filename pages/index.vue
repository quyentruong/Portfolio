<template>
  <div>
    <v-row justify="center" align="center">
      <TabSkills />
    </v-row>
    <Project />
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
