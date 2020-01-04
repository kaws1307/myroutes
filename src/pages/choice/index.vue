<template>
  <div>
    <div class="headCard">
      <label>每日私享歌单</label><br>
      <span>04</span><br>
      <label>2020.01.04</label>
    </div>
    
    <ul>
      <li class="recommendList" v-for="item in recommendList" :key="item">
        <span>{{item.title}}</span><br>
        <image class="avatar" :src="item.avator" />
        <label>来自 {{item.label}} 的推荐</label>
        <div>
          <div class="part1">
            <image class="cover" :src="item.cover" />
          </div>
          <div class="part2">
            <image class="icon" src="/static/images/听书.png" />
            <image class="icon fr" src="/static/images/喜欢1.png" />
            <image class="icon fr" src="/static/images/转发.png" />
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  data () {
    return {
      recommendList: [
        {title:'李荣浩', avator:'/static/images/庆余年.png', label:'00', cover:'/static/images/庆余年.png'},
        {title:'李荣浩', avator:'/static/images/许三观.png', label:'00', cover:'/static/images/蕊希.png'},
        {title:'李荣浩', avator:'/static/images/蕊希.png', label:'00', cover:'/static/images/许三观.png'},
      ]
    }
  },

  methods: {
    
  },

  created () {
    
  }
}
</script>

<style scoped>
div {
  margin: 0;
  padding: 0;
  font-size: 0;
}
.headCard {
  width: 650rpx;
  height: 150rpx;
  background-color: cadetblue;
  border-radius: 20rpx;
  margin: 20rpx auto;
  padding: 25rpx 0;
}
label {
  font-size: 26rpx;
  margin-left: 30rpx;
}
span {
  font-size: 50rpx;
  margin-left: 30rpx;
}
.recommendList {
  width: 650rpx;
  margin: 60rpx auto 0;
}
.avatar {
  width: 40rpx;
  height: 40rpx;
  border-radius: 50%;
  margin-left: 30rpx;
  vertical-align: middle;
}
.cover {
  width: 650rpx;
  border-radius: 20rpx 20rpx 0 0;
  margin-top: 20rpx;
}
.part2 {
  height: 120rpx;
  background-color: darkkhaki;
  border-radius: 0 0 20rpx 20rpx;
}
.icon {
  font-size: 0;
  width: 50rpx;
  height: 50rpx;
  background-color: white;
  border-radius: 50%;
  margin-left: 30rpx;
  margin-top: 20rpx;
  padding: 10rpx;
}
.fr {
  float: right;
  margin-right: 30rpx;
}
</style>
