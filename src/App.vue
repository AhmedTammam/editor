<template>
  <div>
  <medium-editor :text='text' v-on:edit='processEditOperation' custom-tag='div'>
</medium-editor>
</div>
</template>

<script>
import editor from 'vue2-medium-editor'


export default {
  name: 'app',
  components: {
    'medium-editor': editor
  },
  data: () => ({
    text: 'text'
  }),
  methods: {
    processEditOperation: function (operation) {
      this.text = operation.api.origElements.innerHTML
    }
  }
}
</script>

<style>
</style>
