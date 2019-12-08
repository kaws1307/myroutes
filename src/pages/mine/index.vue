<template>
  <div class="background">
    <div class="headBox">
      <view class="userinfo">
        <view class="userinfo-avatar">
          <open-data type="userAvatarUrl"></open-data>
        </view>
        <open-data type="userNickName" class="fontSize"></open-data>
      </view>
    </div>
    <div class="bodyBox">
      <ul>
        <li v-for="item in list" :key="item">
          <img :src='item.img'>
          <span>{{item.content}}</span>
          <img class="fr icon" src='/static/images/箭头.png'>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      list: [
        {img: '/static/images/喜欢.png', content: '我的收藏'},
        {img: '/static/images/歌单.png', content: '我创建的歌单'},
        {img: '/static/images/播放历史.png', content: '播放历史'},
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
.background {
  height: 550px;
  background: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1575810649465&di=13dfe9ea0f6dfcd8f1c47823c4541ee2&imgtype=0&src=http%3A%2F%2Fpic36.nipic.com%2F20131205%2F610812_090741643324_2.jpg') no-repeat;
}
.headBox {
  width: 90%;
  height: 170px;
  background: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1575809637474&di=8bd56b0cfa6dd948b9096f826c47d3bc&imgtype=0&src=http%3A%2F%2Fpic.qiantucdn.com%2F58pic%2F17%2F89%2F75%2F55a71567ccd29_1024.jpg') no-repeat;
  border-radius: 15px;
  margin: 5px auto;
}
.bodyBox {
  width: 100%;
  height: 380px;
  background: white;
}
.userinfo {
  position: relative;
  color: #666;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.userinfo-avatar {
  overflow:hidden;
  display: block;
  width: 160rpx;
  height: 160rpx;
  margin: 20rpx;
  margin-top: 50rpx;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
.fontSize {
  font-size: 14px;
}
ul {
  list-style: none;
}
li {
  position: relative;
  width: 85%;
  height: 50px;
  line-height: 50px;
  margin: 20px auto 10px 30px;
}
img {
  width: 30px;
  height: 30px;
  vertical-align: middle;
}
span {
  display: inline-block;
  font-size: 14px;
  margin-left: 10px;
}
.fr {
  position: absolute;
  top: 38%;
  left: 95%;
}
.icon {
  width: 15px;
  height: 15px;
}
</style>
