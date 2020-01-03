<template>
  <div>
    <!-- <div class="user">
    <div></div>
    </div> -->
    
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
      <view style="padding: 15px;">
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
      title_name: '热门',
      grids: [
        {title: '歌手', image: '/static/images/musician.png'},
        {title: '排行', image: '/static/images/排行榜.png'},
        {title: '分类歌单', image: '/static/images/歌单.png'},
        {title: '电台', image: '/static/images/电台.png'}
      ],
      card: [
        {title: '起风了', extra: '林俊杰', thumb: 'https://i.loli.net/2017/08/21/599a521472424.jpg', content: '好听！', footer: '行走的CD'},
        {title: '起风了', extra: '林俊杰', thumb: 'https://i.loli.net/2017/08/21/599a521472424.jpg', content: '好听！', footer: '行走的CD'},
        {title: '起风了', extra: '林俊杰', thumb: 'https://i.loli.net/2017/08/21/599a521472424.jpg', content: '好听！', footer: '行走的CD'}
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
  border-radius: 5px;
}
</style>
