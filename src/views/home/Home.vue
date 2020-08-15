<template>
  <div id = "home">
  <nav-bar>
    <template v-slot:center><div class="home-nav">购物街</div></template>
  </nav-bar>
  <home-swiper :banners = "banner"></home-swiper>
  <recommend-view :recommend = "recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from '@/components/common/navbar/NavBar'
import HomeSwiper from './childcomponents/HomeSwiper'
import RecommendView from './childcomponents/RecommendView'

import {getMultiData} from '@/network/home'

export default {
  name : 'Home',
  data () {
    return {
      banner : [],
      recommends : []
    }
  },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView
  },
  created () {
    getMultiData ().then(res => {
      this.banner = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  }
}
</script>

<style>
.home-nav {
  color: #fff;
  background-color: var(--color-tint);
}
</style>