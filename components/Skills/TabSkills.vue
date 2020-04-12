<template>
  <v-card width="600" dark>
    <v-card-title>Skills</v-card-title>
    <v-card-text>
      <v-tabs
        v-model="tab"
        dark
      >
        <v-tab v-for="item in items" :key="item.tab">
          {{ item.tab }}
        </v-tab>
      </v-tabs>
      <v-tabs-items v-model="tab" dark>
        <v-tab-item v-for="item in items" :key="item.tab">
          <component :is="item.component" />
        </v-tab-item>
      </v-tabs-items>
    </v-card-text>
  </v-card>
</template>

<script>

import ProgrammingLanguages from './ProgrammingLanguages'
import Application from './Application'
import NativeLanguages from './NativeLanguages'
import SourceControl from './SourceControl'
import OperatingSystem from './OperatingSystem'
import Frameworks from './Frameworks'

export default {
  name: 'TabItem',
  data: () => ({
    tab: null,
    items: [
      {
        tab: 'Programming Language',
        component: ProgrammingLanguages
      },
      {
        tab: 'Application',
        component: Application
      },
      {
        tab: 'Framework',
        component: Frameworks
      },
      {
        tab: 'Source Control',
        component: SourceControl
      },
      {
        tab: 'Operating System',
        component: OperatingSystem
      },
      {
        tab: 'Language',
        component: NativeLanguages
      }
    ]
  })
}
</script>

<style scoped>

</style>
