<template>
  <div id = "recommend-view">
    <div v-for="item in recommend" :key = "item.link" class="recommend-item">
      <a :href="item.link" > 
        <img :src="item.image" alt="" width="80%">
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

<style>
#recommend-view {
  display: flex;
  justify-content: space-around;
  text-align: center;
  margin:15px 0;
  border-bottom: 10px solid #eee;
}
</style>