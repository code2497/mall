<template>
  <div class="tabbar-item" @click = 'pageChange()'>
    <div v-if="!isActive"><slot name="icon"></slot></div>
    <div v-else><slot name="activeImg"></slot></div>
    <div :class="{active : isActive}"><slot name="text"></slot></div>
  </div>
</template>

<script>
export default {
  name : 'TabBarItem',
  props: {
    path : String,
  },
  data () {
    return {
      // isActive : true
    }
  },
  computed: {
    isActive (){
      return this.$route.path.includes(this.path);
    }
  },
  methods: {
    pageChange (){
      this.$router.push(this.path);

    }
  }
}
</script>

<style>
  .tabbar-item {
    flex: 1;
    height: 49px;
    text-align: center;
    font-size: 14px;
    margin-bottom: 3px;
  }

  .tabbar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: center;
  }

  .tabbar-item .active{
    color: red;
  }
</style>