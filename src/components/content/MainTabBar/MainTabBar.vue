<template>
  <tab-bar activeColor = "pink">
      <tab-bar-item path="/home">
        <template v-slot:icon>
          <img src="@/assets/images/tabbar/home.svg" alt="">
        </template>
        <template v-slot:text>
          <div>首页</div>
        </template>
        <template #activeImg>
          <img src="@/assets/images/tabbar/home_active.svg" alt="">
        </template>
      </tab-bar-item>

      <tab-bar-item path="/category">
        <template v-slot:icon>
          <img src="@/assets/images/tabbar/category.svg" alt="">
        </template>
        <template v-slot:text>
          <div>分类</div>
        </template>
        <template #activeImg>
          <img src="@/assets/images/tabbar/category_active.svg" alt="">
        </template>
      </tab-bar-item>

      <tab-bar-item path="/shopcart">
        <template v-slot:icon>
          <img src="@/assets/images/tabbar/shopcart.svg" alt="">
        </template>
        <template v-slot:text>
          <div>购物车</div>
        </template>
        <template #activeImg>
          <img src="@/assets/images/tabbar/shopcart_active.svg" alt="">
        </template>
      </tab-bar-item>

      <tab-bar-item path="/profile">
        <template v-slot:icon>
          <img src="@/assets/images/tabbar/profile.svg" alt="">
        </template>
        <template v-slot:text>
          <div>我的</div>
        </template>
        <template #activeImg>
          <img src="@/assets/images/tabbar/profile_active.svg" alt="">
        </template>
      </tab-bar-item>
    </tab-bar>
</template>

<script>
import TabBar from '@/components/common/TabBar/TabBar'
import TabBarItem from '@/components/common/TabBar/TabBarItem'

export default {
  name : 'MainTabBar',
  components: {
      TabBar,
      TabBarItem
    }
}
</script>

<style>
</style>