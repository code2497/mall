<template>
  <div class="tab-bar-control">
    <div class="tab-bar-control-item" 
        v-for="(item, index) in titles" 
        :key="index"
        :class="{active : currentIndex === index}"
        @click="itemClick(index)"
    >
      <span> {{ item }} </span>
    </div>
  </div>
</template>

<script>
  export default {
    name : 'TabBarControl',
    data () {
      return {
        currentIndex : 0  
      }
    },
    methods : {
      itemClick (index) {
        this.currentIndex = index;
        this.$emit('tabControlClick', index);
      }
    },
    props : {
      titles : {
        type : Array, 
        default () {
          return []
        }
      }
    }
  }
</script>

<style scoped>
.tab-bar-control {
  margin-top: 10px;
  display: flex;
}

.tab-bar-control-item {
  flex: 1;
  text-align: center;
}
.tab-bar-control-item span{
  padding: 3px;
}

.active {
  color: var(--color-high-text);
}

.active span {
  border-bottom: 2px solid var(--color-tint);
} 
</style>