<template>
  <div class="app">
    <div class="block">
      <div id="input-number">
        <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10"></el-input-number>
      </div>
    </div>
    <div class="block">
      <div id="date-time-picker">
        <el-date-picker v-model="date1" type="datetime" placeholder="日時を選択してください">
        </el-date-picker>
      </div>
    </div>
    <div class="block">
      <div id="slider">
        <el-slider v-model="value1" :show-tooltip="true"></el-slider>
        <span id="slider-value">{{value1}}</span>
      </div>
    </div>
    <div class="block">
      <div id="messagebox">
        <el-button :plain="true" @click="open1">成功</el-button>
        <el-button :plain="true" @click="open2">警告</el-button>
        <el-button :plain="true" @click="open3">メッセージ</el-button>
        <el-button :plain="true" @click="open4">エラー</el-button>
      </div>
    </div>
    <div class="block">
      <div id="switches">
        <el-switch v-model="sw1" active-value=8 inactive-value=0></el-switch>
        <el-switch v-model="sw2" active-value=4 inactive-value=0></el-switch>
        <el-switch v-model="sw3" active-value=2 inactive-value=0></el-switch>
        <el-switch v-model="sw4" active-value=1 inactive-value=0></el-switch>
        <span id="switches">{{swvalue}}</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        num1: 1,
        date1: '',
        value1: 50,
        sw1: 0,
        sw2: 0,
        sw3: 0,
        sw4: 0
      }
    },
    methods: {
      handleChange (value) {
        console.log(value)
      },
      open1 () {
        this.$message({
          message: '成功しました',
          type: 'success'
        })
      },
      open2 () {
        this.$message({
          message: '警告です',
          type: 'warning'
        })
      },
      open3 () {
        this.$message({
          message: '普通のメッセージ'
        })
      },
      open4 () {
        this.$message.error({
          message: 'エラーです'
        })
      }
    },
    computed: {
      swvalue: function () {
        return Number(this.sw1) + Number(this.sw2) + Number(this.sw3) + Number(this.sw4)
      }
    }
  }
</script>

<style>
  .block  {
    font-family:  "メイリオ","ヒラギノ角ゴ",sans-serif;
    padding: 30px 24px;
    overflow: hidden;
    border-bottom: 1px solid #eff3f6;
    color: #445566;
  }
  span#slider-value {
    font-size: 20pt;
  }
  span#switches {
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    position: relative; 
    top: 5px;
    left: 20px;
    font-size: 24pt;
  }
</style>
