<template>
  <Swiper>
    <swiper-item v-for="item in banners" :key = "item.link">
      <a :href="item.link"></a>
      <img :src="item.image" alt="">
    </swiper-item>
  </Swiper>
</template>

<script>
import {Swiper, SwiperItem} from '@/components/common/swiper/index'

export default {
  name : 'HomeSwiper',
  props : {
    banners : {
      type : Array, 
      default () {
        return 
      }
    }
  },
  components: {
    Swiper, 
    SwiperItem
  }
}
</script>

<style>

</style>