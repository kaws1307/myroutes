<template>
  <div>
    <i-input :value="val" type="text" mode="wrapped" placeholder="搜索" />

    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="img in imgUrls" :key="img">
        <swiper-item>
          <image class="imgStyle" :src="img" style="width:100%" />
        </swiper-item>
      </block>
    </swiper>

    <i-grid i-class="no-border">
      <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
          <i-grid-icon>
              <image :src="grid.image" />
          </i-grid-icon>
          <i-grid-label>{{grid.title}}</i-grid-label>
      </i-grid-item>
    </i-grid>

    <i-panel title="热门">
      <ul>
        <li class="hot" v-for="item in hotImg" :key="item">
          <image :src="item.image" />
          <span>{{item.title}}</span><br>
          <label>{{item.author}}</label>
        </li>
      </ul>
    </i-panel>

    <i-panel title="精选">
      <view>
        <i-card v-for="item in card" :key="item" i-class="split" :title="item.title" :extra="item.extra" :thumb="item.thumb">
          <view slot="content">{{item.content}}</view>
          <view slot="footer">{{item.footer}}</view>
        </i-card>
      </view>
    </i-panel>
  </div>
</template>

<script>

export default {
  data () {
    return {
      val: '',
      hotImg: [
        {image: '/static/images/蕊希Erin.jpg', title: '蕊希电台', author: '蕊希'},
        {image: '/static/images/程一.jpg', title: '程一电台', author: '程一'},
        {image: '/static/images/张云雷.jpg', title: '张云雷相声小曲', author: '张云雷'},
      ],
      title_name: '热门',
      grids: [
        {title: '主播', image: '/static/images/musician.png'},
        {title: '排行', image: '/static/images/排行榜.png'},
        {title: '分类', image: '/static/images/歌单.png'},
        {title: '一起听', image: '/static/images/电台.png'}
      ],
      card: [
        {title: '一禅小和尚', extra: '一禅小和尚', thumb: '/static/images/一禅小和尚.jpg', content: '再善良，这三件事也不能让', footer: '有问题，找一禅！'},
        {title: '睡前歌一首', extra: '吴大侠', thumb: '/static/images/睡前.jpg', content: '林俊杰：可惜没如果', footer: '这里不是音乐百科，只是和你在临睡前，随便聊聊，分享一下睡前歌，仅此而已。'},
        {title: '为你读诗', extra: '为你读诗', thumb: '/static/images/为你读诗.jpg', content: '杨乃文「为你读诗」：《命运的简单转折》', footer: '为你读诗，给灵魂片刻自由。'}
      ],
      imgUrls: [
        '/static/images/庆余年.png', 
        '/static/images/蕊希.png',
        '/static/images/许三观.png',
        '/static/images/人生.png'
      ],
      indicatorDots: false,
      // vertical: false,
      autoplay: false,
      interval: 2000,
      duration: 500
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
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
.imgStyle {
  border-radius: 10rpx;
}
.hot {
  float: left;
  width: 200rpx;
  height: 300rpx;
  margin: 25rpx;
}
.hot image {
  width: 200rpx;
  height: 200rpx;
  border-radius: 20rpx;
}
span, label {
  font-size: 24rpx;
}
label {
  color: gray;
}
</style>
