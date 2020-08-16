<template>
  <div class="back-to-top">
    <img src="@/assets/images/common/top.png" alt="">
  </div>
</template>

<script>
  export default {
    name : 'BackTop'
  }
</script>

<style scoped>
  .back-to-top {
    position: fixed;
    bottom: 50px;
    right: 10px;
    
    z-index: 9999;
  }

  .back-to-top img {
    width: 43px;
    height: 43px;
  }
</style>