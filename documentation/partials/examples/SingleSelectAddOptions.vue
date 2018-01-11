<template lang="pug">
div
  label.typo__label Select with search
  multiselect(
    v-model="value",
    :options="options",
    :custom-label="nameWithLang",
    :allow-custom="addCustom",
    :preserve-search="true",
    placeholder="Select one",
    label="name",
    track-by="name"
  )
  pre.language-json
    code.
      {{ value  }}
</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  components: {
    Multiselect
  },
  data () {
    return {
      value: { name: 'Vue.js', language: 'JavaScript' },
      options: [
        { name: 'Vue.js', language: 'JavaScript' },
        { name: 'Rails', language: 'Ruby' },
        { name: 'Sinatra', language: 'Ruby' },
        { name: 'Laravel', language: 'PHP' },
        { name: 'Phoenix', language: 'Elixir' }
      ]
    }
  },
  methods: {
    nameWithLang ({ name, language }) {
      return `${name} — [${language}]`
    },

    addCustom (search) {
      let [name, language] = search.split(' ')
      console.log({ name, language })
      return { name, language }
    }
  }
}
</script>

<style lang="css">
</style>
