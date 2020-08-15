<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    activeColor : {
      type : String,
      default : "red"
    }
  },
  created () {
    console.log(this.activeColor);
  },
  name : 'TabBar'
}
</script>

<style>
  #tab-bar {
    background-color: #f6f6f6;
    display: flex;
    position: fixed;
    right: 0;
    left: 0;
    bottom: 0;
    box-shadow: 0 -1px  1px rgba(100, 100, 100, .2);
  }
</style>