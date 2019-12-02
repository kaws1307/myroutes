<template>
  <div>
    <i-card v-for="item in list" :key="item" i-class="split" :title="item.title" :extra="item.extra" :thumb="item.thumb">
      <view slot="content">{{item.content}}</view>
      <view slot="footer">{{item.footer}}</view>
    </i-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      list:[]
    }
  },
  onLoad (option) {
    this.list = require('@/data/' + option.type + '.json')
    console.log(this.list)
  },
  methods: {

  },
  created () {

  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>