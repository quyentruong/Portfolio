<template>
  <GeneralTabItem :items="items" />
</template>

<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'OperatingSystem',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'Windows',
        value: '8'
      },
      {
        name: 'Linux',
        value: '7'
      },
      {
        name: 'MacOS',
        value: '7'
      }
    ]
  })
}
</script>

<style scoped>

</style>
