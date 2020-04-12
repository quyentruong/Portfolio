<template>
  <GeneralTabItem :items="items" />
</template>

<script>
import GeneralTabItem from './GeneralTabItem'
export default {
  name: 'Application',
  components: { GeneralTabItem },
  data: () => ({
    items: [
      {
        name: 'API',
        value: '7'
      },
      {
        name: 'Mobile Android',
        value: '4'
      },
      {
        name: 'Website',
        value: '6'
      },
      {
        name: 'MVC Net Core',
        value: '7'
      },
      {
        name: 'UI',
        value: '4'
      },
      {
        name: 'UX',
        value: '4'
      }
    ]
  })
}
</script>

<style scoped>

</style>
