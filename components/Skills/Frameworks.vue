<template>
  <GeneralTabItem :items="items" />
</template>

<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'Frameworks',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'Laravel',
        value: '5'
      },
      {
        name: 'VueJS/NuxtJS',
        value: '7'
      },
      {
        name: 'NodeJS',
        value: '5'
      },
      {
        name: 'Vuetify',
        value: '6'
      },
      {
        name: 'Bootstrap 4',
        value: '6'
      }

    ]
  })
}
</script>

<style scoped>

</style>
