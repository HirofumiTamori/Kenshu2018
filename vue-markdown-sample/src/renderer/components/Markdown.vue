<template>
  <div id="wrapper">
    <div id="text-area">
      <textarea v-model="text" placeholder="入力してください"></textarea>
    </div>
    <div id="read-button">
      <button @click="loadText">読み込み</button>
    </div>
    <div id="write-button">
      <button @click="saveText">書き出し</button>
    </div>

    <div id="markdown-area">
      <vue-markdown :source="text"></vue-markdown>
    </div>
  </div>
</template>

<script>
import VueMarkdown from 'vue-markdown'
const fs = require('fs')
const {dialog} = require('electron').remote

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
      dialog.showOpenDialog({
        properties: ['openFile'],
        filters: [{name: 'MarkDown', extensions: ['md']}]},
      (fAry) => {
        console.log(fAry)
        fs.readFile(fAry[0], 'utf8', (err, data) => {
          if (err) {
            console.log(err)
            return err
          } else {
            this.text = data
          }
        })
      })
    },
    saveText () {
      console.log('save')
      dialog.showSaveDialog({
        filters: [{name: 'MarkDown', extensions: ['md']}]},
      (f) => {
        console.log(f)
        fs.writeFileSync(f, this.text)
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


