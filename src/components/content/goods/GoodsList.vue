<template>
  <div class="goods">
    <!-- goodsList是数组 -->
    <good-list-item v-for="(item, index) in goodsList"
    :key="index" 
    :goodsListItem="item"></good-list-item>
  </div>
</template>

<script>
import GoodListItem from './GoodListItem'

  export default {
    name : 'GoodsList',
    props : {
      goodsList : {
        type : Array,
        default () {
          return []
        }
      }
    },
    components : {
      GoodListItem
    }
  }
</script>

<style scoped>
  .goods {
    margin-top: 15px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
</style>