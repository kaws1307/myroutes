<template>
  <div class="classification">
    <div class="zone">
      <label>专区</label>
      <ul>
        <li v-for="item in zone" :key="item">
          <img :src="item.img">
        </li>
      </ul>
    </div>
    <div class="recommend">
      <label>推荐分类</label>
      <ul>
        <li v-for="item in recommend" :key="item">{{item.name}}</li>
      </ul>
    </div>
    <div class="music">
      <label>MOO音乐·国风古都</label>
      <ul>
        <li v-for="item in music" :key="item">
          <img :src="item.img">
          <p>{{item.content}}</p>
          <p>{{item.author}}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      zone: [
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/00.jpg'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/01.jpg'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/02.jpg'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/03.jpg'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/04.jpg'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/05.jpg'}
      ],
      recommend:[
        {name: '00年代'},
        {name: '90年代'},
        {name: '80年代'},
        {name: '安静'},
        {name: '运动'},
        {name: '欢快'},
        {name: '伤感'},
        {name: '睡前'},
        {name: '轻音乐'},
        {name: '学习'},
        {name: 'KTV'},
        {name: '热歌'}
      ],
      music: [
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/01.jpg', content: '京味国风·北平那些事儿', author: '蜜糖男孩'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/02.jpg', content: '长安一夜·灯火阑珊', author: '醉枫染墨'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/05.jpg', content: '风韵贯古今', author: '故淮安'},
        {img: 'cloud://kaws1307-30kz7.6b61-kaws1307-30kz7-1301065903/images/01.jpg', content: '国风·水墨江南', author: '蜜糖男孩'},
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
.classification {
  margin: 10px;
}
ul {
  list-style: none;
}
.classification li {
  float: left;
  width: 157px;
  margin: 5px 10px;
}
label {
  font-size: 16px;
  margin-left: 10px;
}
img {
  width: 100%;
  height: 60px;
  border-radius: 5px;
}
.recommend li {
  float: left;
  width: 108px;
  font-size: 14px;
  text-align: center;
  background-color: rgba(250, 246, 241, 0.979);
  border-radius: 5px;
  margin: 5px;
}
p {
  font-size: 14px;
}
</style>
