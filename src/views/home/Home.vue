<template>
  <div id="home">
    <nav-bar>
      <template v-slot:center>
        <div class="home-nav">购物街</div>
      </template>
    </nav-bar>
    <scroll class="scroll" 
            ref="scroll" 
            :proper-type="3"
            :pull-up-load="true"
            @scroll="contentScroll"
            @pullingUp="loadMore">
      <home-swiper :banners="banner"></home-swiper>
      <recommend-view :recommend="recommends"></recommend-view>
      <feature-view></feature-view>
      <tab-bar-control @tabControlClick="tabControlClick" :titles="['哲学', '钕装', '魔法']"></tab-bar-control>
      <goods-list :goodsList="currentGoodsList"></goods-list>
    </scroll>
    <back-top @click.native="backTop"
              v-show="isShowBackTop"
    ></back-top>

    <div>
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
    </div>
  </div>
</template>

<script>
import HomeSwiper from "./childcomponents/HomeSwiper";
import RecommendView from "./childcomponents/RecommendView";
import FeatureView from "./childcomponents/FeartureView";



import TabBarControl from "@/components/content/tabbarcontrol/TabBarControl";
import GoodsList from "@/components/content/goods/GoodsList";
import BackTop from '@/components/content/backtop/BackTop'
import Scroll from "@/components/common/scroll/Scroll";
import NavBar from "@/components/common/navbar/NavBar";

import { getMultiData, getHomeGood } from "@/network/home";

export default {
  name: "Home",
  data() {
    return {
      banner: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
      currentType: "pop",
      isShowBackTop : false
    };
  },
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabBarControl,
    NavBar,
    GoodsList,
    Scroll,
    BackTop
  },
  created() {
    this.getMultiData();
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
  mounted () {
    this.$bus.$on('GoodsImgLoad', ()=> {
      this.$refs.scroll.refresh();
    });
  },
  computed: {
    currentGoodsList() {
      return this.goods[this.currentType].list;
    },
  },
  methods: {
    // 事件监听
    tabControlClick(index) {
      console.log(index);
      switch (index) {
        case 0:
          this.currentType = "pop";
          break;
        case 1:
          this.currentType = "new";
          break;
        case 2:
          this.currentType = "sell";
          break;
      }
    },
    contentScroll (position) {
      this.isShowBackTop = (-position.y) > 1000 ;
    },

    backTop () {
      this.$refs.scroll.scrollTo(0, 0, 1000);
    },

    loadMore () {
      this.getHomeGoods(this.currentType);
      this.$refs.scroll.finishPullUp();
      
    },

    //网络请求方法
    getMultiData() {
      getMultiData().then((res) => {
        this.banner = res.data.banner.list;
        this.recommends = res.data.recommend.list;
        // this.$refs.scroll.refresh();
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGood(type, page).then((res) => {
        this.goods[type].page += 1;
        this.goods[type].list.push(...res.data.list);
      });
      
    },
  },
};
</script>

<style scoped>
#home {
  position: relative;
  height: 100vh;
}


.home-nav {
  color: #fff;
  background-color: var(--color-tint);
}

.scroll {
  overflow: hidden;
  position: absolute;
  top: 44px;
  bottom: 52px;
  left: 0;
  right: 0;
}
</style>

