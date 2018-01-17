<template>
  <div id="wrapper">
    <div id="text-area">
      <textarea v-model="text" placeholder="入力してください"></textarea>
    </div>
    <div id="read-button">
      <button @click="loadText">ロード</button>
    </div>
    <div id="markdown-area">
      <vue-markdown :source="text"></vue-markdown>
    </div>
  </div>
</template>

<script>
import VueMarkdown from 'vue-markdown'
const fs = require('fs')

export default {
  name: 'vuemarkdown',
  data () {
    return {
      text: ''
    }
  },
  components: {
    VueMarkdown
  },
  methods: {
    loadText () {
      console.log('read')
      fs.readFile('initial.md', 'utf8', (err, data) => {
        if (err) {
          console.log(err)
          return err
        } else {
          console.log('reading...')
          this.text = data
        }
      })
    }
  }
}
</script>

<style scoped>
  #text-area {
    width: 650px;
    height: 310px;
  }
  #text-area textarea {
    width: 600px;
    height: 300px;
  }
</style>


