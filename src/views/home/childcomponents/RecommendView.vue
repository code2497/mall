<template>
  <div id = "recommend-view">
    <div v-for="item in recommend" :key = "item.link" class="recommend-item">
      <a :href="item.link" > 
        <img :src="item.image" alt="">
        <div>{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name : 'RecommendView',
  props : {
    recommend : {
      type : Array, 
      default () {
        return []
      }
    }
  }
}
</script>

<style scoped>
.recommend-item img {
  width : 75px;
  height: 75px;
}

#recommend-view {
  display: flex;
  text-align: center;
  margin:15px 0;
  border-bottom: 10px solid #eee;
  justify-content: space-around;
}
</style>