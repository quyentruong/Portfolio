<template>
  <GeneralTabItem :items="items" />
</template>

<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'SourceControl',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'Github',
        value: '8'
      },
      {
        name: 'Azure DevOps',
        value: '6'
      },
      {
        name: 'Bitbucket',
        value: '5'
      }
    ]
  })
}
</script>

<style scoped>

</style>
