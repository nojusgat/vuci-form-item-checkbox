<template>
  <vuci-form-item-template v-bind="VuciFormItemTemplateProps">
    <a-checkbox-group
      v-model="model"
      :options="convertedOptions"
      :name="name"
    />
  </vuci-form-item-template>
</template>

<script>
import VuciFormItemMixin from './VuciFormItemMixin'

export default {
  name: 'VuciFormItemCheckBox',
  mixins: [VuciFormItemMixin],
  props: {
    options: Array
  },
  computed: {
    convertedOptions () {
      const options = []
      this.options.forEach(o => {
        if (o instanceof Object === false && o instanceof Array === false) {
          o = { value: o }
        } else if (o instanceof Object && o instanceof Array) {
          o = o.length < 2 ? { value: o[0] } : { label: o[1], value: o[0] }
        }
        options.push(o)
      })
      return options
    }
  }
}
</script>
