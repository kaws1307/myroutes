<template>
  <div>
    <div class="headCard">
      <label>每日私享歌单</label><br>
      <span>{{date}}</span><br>
      <label>{{year}}.{{month}}.{{date}}</label>
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
          <div class="part2" :style="item.color">
            <image class="icon" src="cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/听书.png" @click="hanlerPaly(item.src)"/>
            <image class="icon fr" src="cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/喜欢1.png" />
            <image class="icon fr" src="cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/转发.png" />
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
      innerAudioContext: null, // 音频对象
      isPaly: false, // 是否播放
      sliderProgress: 0, // 滑动控制条进度
      year: "",
      month: "",
      date: "",
      recommendList: [
        {title:'庆余年|余年有幸，与君相逢', avator:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/庆余年.png', label:'liangliang', cover:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/庆余年.png', color:'background:gray',src:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/audio/片花 (节目).mp3'},
        {title:'SPA解压室', avator:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/许三观.PNG', label:'00', cover:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/蕊希.png', color:'background:pink',src:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/audio/程一 - 让我做你的小太阳吧【戴耳机听】 (节目).mp3'},
        {title:'每天晚上和你一起说晚安', avator:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/蕊希.png', label:'小邋遢', cover:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/01.jpg', color:'background:#5E87A2',src:'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/audio/蕊希Erin.mp3'},
      ]
    }
  },
  created() {
    this.getDate()
     // 创建音频播放对象
    this.innerAudioContext = wx.createInnerAudioContext()
    // 设置音频播放来源
    this.innerAudioContext.src = this.recommendList[2].src
    // 音频进入可以播放状态
    this.innerAudioContext.onCanplay((res) => {
      this.isPaly = false
    })
    // 音频自然播放结束事件
    this.innerAudioContext.onEnded((res) => {
      // 当音频播放结束后，将滑动条滑到末尾
      this.sliderProgress = 100
      this.isPaly = false
    })
  },
  destroyed () {
    this.innerAudioContext.destroy()
  },
  methods: {
    getDate(){
      var time = new Date()
      var year = time.getFullYear()
      var month = time.getMonth()+1
      var date = time.getDate()
      this.year = year
      this.month = month
      this.date = date
    },

    // 播放暂停
    hanlerPaly () {
      this.isPaly = !this.isPaly
    }
  },
  
  watch: {
    isPaly (val, oldVal) {
      this.innerAudioContext.offCanplay()
      if (val) {
        this.innerAudioContext.play()
      } else {
        this.innerAudioContext.pause()
      }
    }
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
  font-size: 40rpx;
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
  height: 300rpx;
  border-radius: 20rpx 20rpx 0 0;
  margin-top: 20rpx;
}
.part2 {
  height: 120rpx;
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
.bottom {
  position: fixed;
  bottom: 0;
  padding: 0 80rpx;
}
</style>
