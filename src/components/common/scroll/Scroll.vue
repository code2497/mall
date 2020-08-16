<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import bScroll from 'better-scroll'

  export default {
    name : 'Scroll',
    props : {
      properType : {
        type : Number,
        default () {
          return 0
        }
      },
      pullUpLoad : {
        type : Boolean,
        default () {
          return false
        }
      }
    },
    data () {
      return {
        scroll : null
      }
    },
    mounted () {
      this.scroll = new bScroll (this.$refs.wrapper,{
        probeType : this.properType, 
        click : true, 
        pullUpLoad : this.pullUpLoad
      });


      // 监听滚动
      if(this.properType === 3 || this.properType === 2 ){
        this.scroll.on('scroll', position => {
          this.$emit('scroll', position);
        });
      }

      // 监听下拉到尽头
      if(this.pullUpLoad) {
        this.scroll.on('pullingUp', () => {
          this.$emit('pullingUp')
        })
      }

      

    },
    methods : {
      scrollTo (x, y, time = 500) {
        this.scroll.scrollTo(x, y, time);
      },

      finishPullUp () {
        this.scroll.finishPullUp();
      },

      refresh () {
        this.scroll.refresh();
      },
    }
  }
</script>

<style scoped>

</style>