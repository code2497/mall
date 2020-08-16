<template>
  <div class="goods-list-item">
    <img :src="goodsListItem.show.img" alt="" @load="GoodsImgLoad">
    <div class="goods-item-info">
      <p> {{ goodsListItem.title }} </p>
      <span class="fav"> {{ goodsListItem.cfav }} </span>
      <span class="price"> {{ goodsListItem.price }} </span>
    </div>
  </div>
</template>

<script>
  export default {
    name : 'GoodListItem',
    props : {
      goodsListItem : {
        type : Object,
        default () {
          return {};
        }
      }
    },
    methods : {
      GoodsImgLoad () {
        this.$bus.$emit('GoodsImgLoad');
      }
    }
  }
</script>

<style scoped>
.goods-list-item {
  width: 45%;
  margin-bottom: 10px;
  text-align: center;
}

.goods-list-item img {
  width: 100%;
}

.goods-list-item p {
  overflow: hidden;
  white-space: nowrap;
  text-overflow:ellipsis;
  font-size: 13px;
}

.goods-list-item .fav {
  position: relative;
  font-size: 12px;
}

.goods-list-item .fav::before {
  position: absolute;
  width: 14px;
  height: 14px;
  left: -14px;
  top: 0;
  content: '';
  background: url(/img/collect.eb1f91fb.svg) 0 0/14px 14px;
  background-position: 0 0 ;
}
.goods-list-item .price {
  font-size: 14px;
  color: var(--color-high-text);
  font-weight: bold;
}
</style>