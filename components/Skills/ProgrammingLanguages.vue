<template>
  <GeneralTabItem :items="items" />
</template>

<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'Languages',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'C#',
        value: '6'
      },
      {
        name: 'Python',
        value: '5'
      },
      {
        name: 'HTML',
        value: '5'
      },
      {
        name: 'JavaScript',
        value: '6'
      },
      {
        name: 'CSS',
        value: '4'
      },
      {
        name: 'PHP',
        value: '3'
      },
      {
        name: 'Java',
        value: '5'
      },
      {
        name: 'SQL/MySQL',
        value: '5'
      }
    ]
  })
}
</script>

<style scoped>

</style>
