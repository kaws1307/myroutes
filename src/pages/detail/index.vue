<template>
  <div>
    <div class="headerBox">
      <image :src="list[0].img" />
      <div class="frBox">
        <span>{{list[0].name}}</span><br>
        <label>{{list[0].author}}</label>
        <i-tag>+ 关注</i-tag>
        <br>
        <label>{{list[0].introduce}}</label>
      </div>
      <br>
      <i-icon type="like" size="30" class="icon" color="white" />
      <label>{{list[0].like}}万</label>
      <i-icon type="message" size="30" class="icon" color="white" />
      <label>{{list[0].comment}}</label>
      <i-icon type="send" size="30" class="icon" color="white" />
      <label>分享</label>
    </div>
    
    <i-cell-group>
      <i-cell v-for="item in list" :key="item" :title="item.song" is-link></i-cell>
    </i-cell-group>
  </div>
</template>

<script>
export default {
  data () {
    return {
     detail:[],
     list:[]
    }
  },
  onLoad (option) {
    console.log(option)
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
.headerBox {
  width: 750rpx;
  height: 450rpx;
  background: #CDAA7D;
}
image {
  width: 250rpx;
  height: 250rpx;
  border-radius: 20rpx;
  margin: 50rpx;
}
.frBox {
  position: absolute;
  top: 50rpx;
  right: 20rpx;
  width: 370rpx;
  height: 250rpx;
  line-height: 50rpx;
}
span {
  font-size: 40rpx;
  color: white;
}
label {
  font-size: 26rpx;
  color: white;
}
.icon {
  margin-left: 40rpx;
}
.headerBox label {
  margin-right: 80rpx;
}
</style>