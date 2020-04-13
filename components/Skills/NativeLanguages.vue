<template>
  <GeneralTabItem :items="items" />
</template>
<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'NativeLanguages',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'Vietnamese',
        value: 10
      },
      {
        name: 'English Speaking',
        value: 6
      },
      {
        name: 'English Reading',
        value: 8
      },
      {
        name: 'English Writing',
        value: 7
      }
    ]
  })
}
</script>

<style scoped>

</style>
